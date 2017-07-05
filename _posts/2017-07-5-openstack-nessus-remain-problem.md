---
title: OpenStack Nessus 扫描隐患分析
tags: openstack, nessus, security, it, cloud
notebook: INESA
layout: post
category: tech
author: "Pengfei Zhang"
---

在解决了OpenStack中一系比较重要的安全隐患之后（[见前面的Post](http://zionpf.github.io/2017/04/nessus-openstack-solution)），Nessus扫描仍然遗留了几个风险警告，但是已经不影响系统的安全和运营，下面是相关漏洞的描述与说明。

## AMQP Cleartext Authentication

描述：AMQP 消息队列服务中允许明文鉴权

风险：Medium

说明：开源OpenStack中的AMQP 消息队列默认配置，消息队列仅提供相应的内网服务组件，且后端有进一步的认证授权机制（Keystone），故不影响系统运行安全。

## SSL 相关：

SSL 相关的几个Medium漏洞，均为老版本SSL对于一些加密方式的支持导致，在i-stack环境中，相应的加密方式足以支持系统安全。Nessus已经在最新企业版本中取消了相关的 SSL3.0 的支持，故下述相应漏洞在i-stack环境中均无显著风险。

* SSL Version 2 and 3 Protocol Detection

    - 描述：发现SSL 较早期版本2，3

    - 风险：Medium

    - 说明：为兼容早期版本，需要保留。每个连接可以允许的请求有限的情况下，不影响加密安全。

* SSL Medium Strength Cipher Suites Supported

    - 描述：发现支持中等强度的SSL加密

    - 风险：Medium

    - 说明：实际系统未使用此加密。且对于内网环境，每个连接可以允许的请求有限的情况下，中等强度

    - 加密满足运营需求。

* SSL 64-bit Block Size Cipher Suites Supported (SWEET32)

    - 描述：支持64比特块加密，可能有中间人攻击风险

    - 风险：Medium


    - 说明：实际系统未使用此加密。且在内网环境中，每个连接可以允许的请求有限的情况下，不易被破解，满足运营需求。

* SSLv3 Padding Oracle On Downgraded Legacy Encryption Vulnerability
(POODLE)

    - 描述：SSL 3.0 中的安全隐患，可能有中间人攻击风险

    - 风险：Medium

    - 说明：实际系统未使用此加密。且在内网环境中，每个连接可以允许的请求有限的情况下，不易被破解，满足运营需求。

* SSL RC4 Cipher Suites Supported (Bar Mitzvah)

    - 描述：远程服务支持RC4加密，其在随机字符串的随机性上有缺陷，导致被破解的概率变高

    - 风险：Low

    - 说明：实际系统未使用此加密。且在内网环境中，每个连接可以允许的请求有限的情况下，不易被破解，满足运营需求。

* SSL/TLS Diffie-Hellman Modulus <= 1024 Bits (Logjam)

    - 描述：远程连接中，允许了小雨1024比特的 Diffie-Hellman 

    - Modulus。导致第三方有可能在有限时间内进行破解。

    - 风险：Low

    - 说明：实际系统未使用此加密。且在内网环境中，每个连接可以允许的请求有限的情况下，不易被破解，满足运营需求。

## Web Server 相关漏洞

主要Nessus分析WebServer对外暴露的接口，查看其中有明文传输认证信息的可能性等。实际系统中并无明文密码传递，故无此风险。

* Web Server Generic XSS

    - 描述：Web服务器不能识别及清除特定的含有恶意字符串的 JavaScript 请求。

    - 风险：Medium

    - 说明：系统后台对不符合鉴权与规格的请求有过滤和拒绝的能力。满足运营需求。

*  Web Server Generic Cookie Injection

    - 描述：Web服务器允许了特定的恶意字符串JavaScript 请求，可能导致Cookie注入风险。

    - 风险：Medium

    - 说明：系统后台对不符合鉴权与规格的请求有过滤和拒绝的能力。满足运营需求。

*  Browsable Web Directories

    - 描述：Web服务器中的某些路径文件夹可以在浏览器中显示。

    - 风险：Medium

    - 说明：出现该风险的节点为虚拟IP（216），其上的Web Server以及相应的可浏览文件夹不暴露重要信息。

*  Web Server Transmits Cleartext Credentials

    - 描述：Web服务器可能存在传输明文认证信息的可能。

    - 风险：Low

    - 说明：系统认证信息统一加密处理，Web 服务器所传明文均为正常数据，无泄漏风险。

*  Web Server Uses Basic Authentication Without HTTPS

    - 描述：Web服务器可能存在传输明文认证信息的可能。

    - 风险：Low

    - 说明：系统认证信息统一加密处理，Web 服务器所传明文均为正常数据，无泄漏风险。