---
layout: post
title: "双网卡同子网的VPN服务器ping包不回应问题"
description: ""
category: tech
author: "Pengfei Zhang"
tags : [VPN, NIC, network]
---

对于之前搭建的双网卡VXLAN隧道VPN服务器，发现内网IP无法ping通该服务器内网地址。本文为原因查找解决的总结，以及总结新版本centos中rp_filter 的参数变动。


## 问题描述：

对于如下结构网络：

内网 10.19.30.12 无法 ping 通其网关 10.19.30.7

![VPN_configure](https://github.com/ZionPF/Pictures/blob/master/inesa/vpn_feile_configure.jpg?raw=true)



## 问题分析：

网关为VPN服务器，具有两块网卡 10.19.30.7 （br1-eth1） 与 10.19.30.8(eth0)

该机器收到了来自 12 的 ICMP request，但是无 reply

原因是：默认路由为 10.19.30.8 所在的 eth0 ，因此造成ICMP的收发报文路径不同，在CentOS的默认安全策略下，这是不允许的

从下面结果可以看到，路由上确实是报文 eth1 进， eth2 出

    # ip r
    default via 10.19.30.254 dev eth0
    10.10.0.0/24 dev br1  scope link
    10.19.30.0/24 dev eth0  proto kernel  scope link  src 10.19.30.8
    10.19.30.0/24 dev br1  proto kernel  scope link  src 10.19.30.7
    169.254.0.0/16 dev eth0  scope link  metric 1002
    192.168.122.0/24 dev virbr0  proto kernel  scope link  src 192.168.122.1
    224.0.0.0/4 dev br1  scope link

## 问题解决：

参考以下链接，

[https://access.redhat.com/site/solutions/53031](https://access.redhat.com/site/solutions/53031)
执行：

    # echo 2 > /proc/sys/net/ipv4/conf/default/rp_filter
    # echo 2 > /proc/sys/net/ipv4/conf/all/rp_filter

修改rp_filter 安全策略。（以上修改未固化，重启实效，如确定固化需要参考上述链接中的进一步描述）

## 附：rp_filter 的定义：

/usr/share/doc/kernel-doc-2.6.32/Documentation/networking/ip-sysctl.txt

    rp_filter - INTEGER
            0 - No source validation.
            1 - Strict mode as defined in RFC3704 Strict Reverse Path 
                Each incoming packet is tested against the FIB and if the interface
                is not the best reverse path the packet check will fail.
                By default failed packets are discarded.
            2 - Loose mode as defined in RFC3704 Loose Reverse Path 
                Each incoming packet's source address is also tested against the FIB
                and if the source address is not reachable via any interface
                the packet check will fail.

            Current recommended practice in RFC3704 is to enable strict mode 
            to prevent IP spoofing from DDos attacks. If using asymmetric routing
            or other complicated routing, then loose mode is recommended.

            The max value from conf/{all,interface}/rp_filter is used 
            when doing source validation on the {interface}.

            Default value is 0. Note that some distributions enable it
            in startup scripts.
