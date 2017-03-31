---
layout: post
title: "开源数据分析平台介绍"
description: ""
category: tech
author: "Pengfei Zhang"
tags : [open source, cloud, bigdata, survey, data mining]
---

目前，数据分析成为众多数据科学家以及业界决策人的必备能力，而数据分析的方法也从原来的各类自己编写的程序包扩展到了方便大众使用的数据分析平台和工具。本文介绍几个这方面比较领先的开源平台。本文目录如下：


**调研人：张鹏飞**






<!-- MarkdownTOC -->

- [开源平台](#开源平台)
    - [RapidMiner](#rapidminer)
    - [KNIME](#knime)
    - [Orange](#orange)
    - [Weka](#weka)
- [几个平台的对比情况：](#几个平台的对比情况：)
    - [各平台支持功能比较](#各平台支持功能比较)
    - [各平台发展比较](#各平台发展比较)

<!-- /MarkdownTOC -->



<a name="开源平台"></a>
## 开源平台
先来看一下Gartner的曲线：

![gartner_mining](https://1xltkxylmzx3z8gd647akcdvov-wpengine.netdna-ssl.com/wp-content/uploads/2016/02/med-res-gmq-dsp.jpg)

在 Leader象限，除了IBM和SAS，有两个开源的平台很瞩目：RapidMiner 和 KNIME ，我们先介绍这两个平台，然后再介绍两个相似功能的开源平台。本次调研的开源数据分析平台有：




1. RapidMiner
2. KNIME
3. Orange
4. Weka


<a name="rapidminer"></a>
### RapidMiner

![rapidminer_logo](https://1xltkxylmzx3z8gd647akcdvov-wpengine.netdna-ssl.com/wp-content/uploads/2016/06/rapidminer-logo-retina.png)

[RapidMiner](https://rapidminer.com/), 以前叫 YALE (Yet Another Learning Environment), 其是一个给机器学习和数据挖掘和分析的试验环境，同时用于研究了真实世界数据挖掘。它提供的实验由大量的算子组成，而这些算子由详细的XML 文件记录，并被RapidMiner图形化的用户接口表现出来。RapidMiner为主要的机器学习过程提供了超过500算子，并且，其结合了学习方案 和Weka学习环境的属性评估器。它是一个独立的工具可以用来做数据分析，同样也是一个数据挖掘引擎可以用来集成到你的产品中。

优点：
 
* 较全的支持
* 功能和服务支持较全面。
* 回归、高斯等统计工具易用程度好

缺点：

* 功能非常多，新手上手慢

成功案例：

* Cisco
* Paypal
* Ebay
* Miele
* VolksWagen


![rapirminer_example](https://www.whatasoftware.com/app/webroot/img/software/original/1456387129_rapidminer1.png)


<a name="knime"></a>
### KNIME

![knime_logo](https://encrypted-tbn3.gstatic.com/images?q=tbn:ANd9GcRmi9IRKt93MjW7aApviBLICCiNFzKRxLxc6u7YEmpenwSXAa-71IrF-k0)

[KNIME (Konstanz Information Miner)](https://www.knime.org/) 是一个用户友好，智能的，并有丰演的开源的数据集成，数据处理，数据分析和数据勘探平台。它给了用户有能力以可视化的方式创建数据流或数据通道，可选择性 地运行一些或全部的分析步骤，并以后面研究结果，模型 以及 可交互的视图。 KNIME 由Java写成，其基于 Eclipse 并通过插件的方式来提供更多的功能。通过以插件的文件，用户可以为文件，图片，和时间序列加入处理模块，并可以集成到其它各种各样的开源项目中，比如：R 语言，Weka， Chemistry Development Kit, 和 LibSVM.

优点：

* 基于JAVA, 方便跨平台
* 新手易用性好，不需要特殊的数据分析知识

This is built on JAVA platform which makes it compatible in all the Systems including Linux, Windows and Mac. This is designed in such a way, even people who do not have experience on coding and Analysis can easily handle this tool. For more Molecular Analysis KNIME is the best fit and also for any other Science Analyst.


![knime_example](https://www.knime.org/files/images/products/AnalyticsPlatform/knime-analytics-platform.png)

<a name="orange"></a>
### Orange

![orange_logo](http://orange.biolab.si/static/images/orange_logo_new.png)

[Orange](http://orange.biolab.si/) 是一个基于组件的数据挖掘和机器学习软件套装，它的功能即友好，又很强大，快速而又多功能的可视化编程前端，以便浏览数据分析和可视化，基绑定了 Python以进行脚本开发。它包含了完整的一系列的组件以进行数据预处理，并提供了数据帐目，过渡，建模，模式评估和勘探的功能。其由C++ 和 Python开发，它的图形库是由跨平台的Qt框架开发。

应用案例：

* Astra-Zeneca, 医药行业巨头，在医药研发／监管方面使用Orange
* Jozef Stefan

优点：

* 新手友好，界面易用
* 可视化界面可以交互

缺点：

* 缺少经典统计插件
* 跨平台兼容性差


![orange_example](http://orange.biolab.si/static/homepage/screenshots/images/tree-explorative.png)



<a name="weka"></a>
### Weka

![weka_logo](https://upload.wikimedia.org/wikipedia/commons/0/07/Weka_%28software%29_logo.png)

[Weka 全称怀卡托智能分析环境（Waikato Environment for Knowledge Analysis）](http://www.cs.waikato.ac.nz/ml/weka/)，是一款开源、免费的机器学习和数据挖掘软件。Weka项目从1992年开始，由新西兰政府支持，现在已在机器学习领域大名鼎鼎。Weka里有非常全面的机器学习 算法，包括数据预处理、分类、回归、聚类、关联规则等。Weka的图形界面对不会写程序的人来说非常方便，而且提供“KnowledgeFlow” 功能，允许将多个步骤组成一个工作流。另外，Weka也允许在命令行执行命令。 

开发语言是java，基于GNU General Public License协议。开源的weka功能不算最多，但是很全，最重要的是文档充裕（中文的较少）同时扩展便利，非常适合学习和研究。

优点：

* 适合初学这，weka explorer极易上手
* 与各数据库接口齐全
* R 语言支持 weka 一些功能，容易整合

缺点

* 没有拖拽形式的数据流设计

![weka_example](http://ithelp.ithome.com.tw/upload/images/20140919/20140919191648541c10a0aea4b_resize_600.png)

<a name="几个平台的对比情况："></a>
## 几个平台的对比情况：

参考文献：[An overview of free software tools for general
data mining](https://pdfs.semanticscholar.org/65fd/dc055a2b7511f7c9a5a1eead16defa9e7390.pdf)

<a name="各平台支持功能比较"></a>
###各平台支持功能比较
![几大功能比较](https://github.com/HolySparky/Pictures/blob/master/inesa/advanced_support_opemML.png?raw=true)

<a name="各平台发展比较"></a>
###各平台发展比较

![各平台发展比较](https://github.com/HolySparky/Pictures/blob/master/inesa/open_sourceML_table.png?raw=true)



