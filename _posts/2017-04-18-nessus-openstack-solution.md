---
title: OpenStack 全节点扫描的漏洞结果及解决方案
tags: openstack, nessus, security, it, cloud
notebook: INESA
layout: post
category: tech
author: "Pengfei Zhang"
---

[Nessus](http://www.tenable.com/products/nessus-vulnerability-scanner) 是目前全世界最多人使用的系统漏洞扫描与分析软件, 使用Nessus对OpenStack环境进行安全漏洞的扫描，发现了以下几个安全隐患，下面是针对性的解决方法，仅供参考




- [HTTP 漏洞](#http-漏洞)
- [SSH安全漏洞](#ssh安全漏洞)
- [mDNS漏洞](#mdns漏洞)
- [VNC认证漏洞](#vnc认证漏洞)
- [SSL相关漏洞](#ssl相关漏洞)




<a name="http-漏洞"></a>

## HTTP 漏洞

漏洞名：

* [MEDIUM：HTTP TRACE / TRACK Methods Allowed](http://www.nessus.org/plugins/index.php?view=single&id=11213)


问题描述：

* HTTP服务中允许了 TRACE/TRACK 方法

解决方法：

在 Apache2 的配置文件 httpd.conf 末尾，加入 TraceEnable Off ：

`TraceEnable Off`

重启httpd服务：

`service httpd restart`



<a name="ssh安全漏洞"></a>

## SSH安全漏洞

漏洞名：

* [Medium:SSH Weak Algorithms Supported](http://www.tenable.com/plugins/index.php?view=single&id=90317)
* [Low: SSH Server CBC Mode Ciphers Enabled](http://www.nessus.org/plugins/index.php?view=single&id=70658)
* [Low: SSH Weak MAC Algorithms Enabled](http://www.nessus.org/plugins/index.php?view=single&id=71049)

问题描述：

* SSH的加密方面使用了安全性较弱的配置。这三个漏洞都是针对SSH安全性的，如下解决即可。


解决方案：


修改：/etc/ssh/sshd_config ,增加：

```
Ciphers aes128-ctr,aes192-ctr,aes256-ctr

MACs hmac-sha1,hmac-ripemd160
```

重启服务：

```
/bin/systemctl restart  sshd.service
```



<a name="mdns漏洞"></a>

## mDNS漏洞

漏洞名：

* [Medium: mDNS Detection (Remote Network)](http://www.nessus.org/plugins/index.php?view=single&id=12218)

问题描述：

* 服务器开启了 mDNS 服务，而这个服务允许局域网其他用户可以获取一些额外的信息（如hostname，机器配置等）

解决方案：

关闭mDNS服务
```
service avahi-daemon stop        #停止avahi-daemon服务
chkconfig avahi-daemon off       #防止avahi-daemon开机再次运行
```


<a name="vnc认证漏洞"></a>

## VNC认证漏洞

漏洞名：

* [High: VNC Server Unauthenticated Access](http://www.nessus.org/plugins/index.php?view=single&id=26925)
* [High: VNC Server Unauthenticated Access: Screenshot](http://www.nessus.org/plugins/index.php?view=single&id=66174)

问题描述：

* 由于OpenStack 的VNC服务开启，允许了无授权访问，因此有隐患

解决方案：

除了Controller节点以外，阻止其他任何IP访问VNC的相应服务端口，修改所有计算节点的iptables：

注释掉下面entry：

`#-A INPUT -p tcp -m tcp --dport 5900:5999 -j ACCEPT`

添加如下几条：

-A INPUT -s 172.35.0.103/32 -p tcp -m multiport --dports 5900:5999 -m comment --comment "001 nova compute incoming nova_compute" -j ACCEPT

-A INPUT -s 172.35.0.104/32 -p tcp -m multiport --dports 5900:5999 -m comment --comment "001 nova compute incoming nova_compute" -j ACCEPT

-A INPUT -p tcp -m tcp --dport 5900:5999 -j REJECT


<a name="ssl相关漏洞"></a>

## SSL相关漏洞

漏洞名：

* [Medium: SSL Certificate Cannot Be Trusted](http://www.nessus.org/plugins/index.php?view=single&id=51192)
* [Medium: SSL Self-Signed Certificate](http://www.nessus.org/plugins/index.php?view=single&id=57582)
* [Medium: SSL Medium Strength Cipher Suites Supported](http://www.nessus.org/plugins/index.php?view=single&id=42873)
* [Medium: SSL 64-bit Block Size Cipher Suites Supported (SWEET32)](http://www.nessus.org/plugins/index.php?view=single&id=90317)

问题描述：

* 该漏洞见于控制节点
* 原因是pcsd 服务允许了不安全的SSL连接

解决方案：


关闭pcsd服务，在所有控制节点执行以下命令：
```
systemctl stop pscd.service
systemctl disable pscd.service
```











