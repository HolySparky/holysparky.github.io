---
title: SODA 2016 决赛队伍创意总结
tags: soda, data, top10
notebook: INESA
layout: post
category: tech
author: "Pengfei Zhang"
---


整理了一下SODA2016比赛的前十队伍工作和决赛表现,看看大数据和开放数据如何启发智慧城市的创新应用。

个人比较感兴趣的几个项目（跟智慧城市、环境、食品安全最相关和有启发的）：

[e图商圈](#e图商圈)，[环境安全可视分析系统](#环境安全可视分析系统)，[评安食客](#评安食客)，[智慧防霾](#智慧防霾)

以下是决赛队伍的工作概述和简单评论。

- [基于大数据分析的上海地区犯罪指数预控与警力配调优化](#基于大数据分析的上海地区犯罪指数预控与警力配调优化)
- [城市金融安全侠](#城市金融安全侠)
- [深度学习下的城市影像分析](#深度学习下的城市影像分析)
- [公共场所人群风险管理与疏散优化系统](#公共场所人群风险管理与疏散优化系统)
- [e图商圈](#e图商圈)
- [环境安全可视分析系统](#环境安全可视分析系统)
- [评安食客](#评安食客)
- [智慧防霾](#智慧防霾)
- [Changify](#changify)
- [优尼克\(Unique\)：智能感知城市安全宜居服务系统](#优尼克unique：智能感知城市安全宜居服务系统)


<a name="基于大数据分析的上海地区犯罪指数预控与警力配调优化"></a>

## 基于大数据分析的上海地区犯罪指数预控与警力配调优化

* 队伍：老和山极客

* 摘要：针对城市犯罪热点鱼预测问题，开发了一个面向警方使用的综合监控平台，以实现可视化的历史案件回溯，精准的犯罪热点预测，短／中／长期的经历部署与调度优化。
在开发时，“老和山极客”团队主要使用了SODA开放的犯罪数据、派出所数据等资源，此外他们还融合了百度API的地理信息数据、上海天气数据、交通卡数据、网络舆情数据等，打造了一个基于数据挖掘和机器学习技术，通过自学习实现犯罪监控、热点预测和警力调配的智能警务系统。

* 点评：故事清晰，可视化有特色。
* 问题：预测部分有些强行了，不过鉴于现在的思路都是事前-事中-事后，也可以理解。

[决赛视频](https://mp.weixin.qq.com/s?__biz=MzA5NjE1ODU1MQ==&mid=2649498869&idx=1&sn=d37fea419958a3e853d8d1573eaf8ca4&chksm=88acd2cdbfdb5bdbf0bbd1e0267aea2b71de19338448dcfd7374b27afd4c988ba090fa0bed84&scene=0&key=614fe289256a5ad88bd86d137778d642a8b6b010fbc8e995c89db2a5e9f7348a071656689546e1eb02235ceb1db73257992b82228ed11e9d775fe812486293017028db434b62fab6ed5fca25e26196b2&ascene=0&uin=MTM0NDQxNjYwMA%3D%3D)



![未来战警](http://mmbiz.qpic.cn/mmbiz_gif/bMX5EkeMvZ3Ly4DhMcfjc3hHs3YCc2OxZdFrjiaa60hQnuvmBD3rjytvsef8fmsAgfiaiaNKtUVjmox15jN8JXicVg/0?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)


<a name="城市金融安全侠"></a>

##城市金融安全侠

* 队伍：电信银策联队

* 摘要：对于目前城市生活中愈加严重的金融诈骗问题，形成大数据反金融诈骗数据库和分析引擎，简历金融诈骗的“事前-事中-事后“解决方案。
 
* 实现：以真实诈骗数据为样本，结合了手机的通讯数据和银行卡消费数据两部分来源，分析了基于通话时长、频次、生命周期、交互维度的用户通讯行为以及基于转账、消费、取现时间、额度等用户资金行为后，用机器学习的方法描摹出诈骗人的画像。之后，通过决策树的分类算法不断迭代优化，提高数据辨认的准确度。最终，模型对大量的用户进行分类，构建“诈骗人号码库”和“骚扰人号码库”两个数据库，方便电信运营商、公安机关、普通民众对诈骗信息进行快速、准确的甄别。

* 点评：故事有，但是数据不够，产品也没做出来。没有可视化展示

[决赛视频](https://mp.weixin.qq.com/s?__biz=MzA5NjE1ODU1MQ==&mid=2649498885&idx=1&sn=bb907fae5d015c31fc6511b09215cadc&chksm=88acd33dbfdb5a2bfd9f0ae7b5e7f468bb425432fec6984d3abbf7e24e6ea6aa3cfc4ebcd283&scene=0&key=fbf9e68652914f9834206d7cd28a609b72c16cedfeb2a7904a7681eed0cc65fb0c44c6c5e4baa5a21128c233ef4a51dbcf8a32c2970fbfcb2b41af5123de4648067652ccce89aad8493d252b0eb01d8c&ascene=0&uin=MTM0NDQxNjYwMA%3D%3D)

![城市金融安全](https://mmbiz.qpic.cn/mmbiz_png/bMX5EkeMvZ0gooe628GwVBhUf2b7BlxdhiceicVVcGCjiaIYW7OqysGK7oU5bMcrktAp08xibeYX1kQPQ9x1hibuibyA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1)





<a name="深度学习下的城市影像分析"></a>

##深度学习下的城市影像分析

* 队伍：StreeTalk

* 摘要：基于soda提供的街道整治数据，准备的街景照片数据，依托深度学习神经网络进行图片特征提取以及寄去学习分类预测算法实现城市街边“非正规摊贩”地图，以及街道安全感地图。


* 实现方法：利用人工标定的街道安全感数据做训练，通过对城市影像的数据库的深度学习，对街道图片安全感打分，并关联到地图中。

* 点评：出发点有特色，深度学习和图像识别技术成熟。

[决赛视频](https://mp.weixin.qq.com/s?__biz=MzA5NjE1ODU1MQ==&mid=2649498896&idx=1&sn=8c75ddc8a9840d9fbf2daf609248e86a&chksm=88acd328bfdb5a3eef7b56da9b9f7348b57dacf49ce96d566c09fd7f933ee0d2752c0c6c1f52&scene=0&key=c24f0790966abbc7b1370327e40caa0492f17dcceae55159d7a0f9a7b36a270eaec5d3e8570d478249ee692b5c40bdac5f268661b09f529c8fa085e0d8648b4d7e1dc4b71fcf03624694861af6ad14da&ascene=0&uin=MTM0NDQxNjYwMA%3D%3D)

![streettalk](https://mmbiz.qpic.cn/mmbiz_png/bMX5EkeMvZ3kFm2Qo8HoFX2BfObtcz0hRHdP5PdIcVKmiala4Q1xgxntiadGpEfOTSE7ibicQiccvE1wIU1WPGXDwRA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1)


<a name="公共场所人群风险管理与疏散优化系统"></a>

##公共场所人群风险管理与疏散优化系统

* 队伍： Innotech

* 摘要：公共场所人群预警与应急疏散系统，目标是基于大数据和人工智能技术，提供上海公共场所人群疏散设计评估、日常运行、应急突发智慧的完整解决方案。

* 实现方法：乘客在站时间的缺失，是Innotech团队在算法上遇到的第一个困难。在这次比赛中，虽然SODA提供的交通卡数据量很大，但内容记录上只有进出站的时间，并没有明确的乘客上车时间和换乘时间，这也就意味着无法准确得知乘客的在站时间，从而估算车站内的人流情况。于是，他们使用了基于神经网络和路径优化的算法，逐条分解了上亿条乘客行程记录，以平均误差最小化为目标，估算出乘客在站时间和地铁站的在站人数。接下来，要实现对地铁人流的有效管理，还需要对实际人数进行分级评估。Innotech团队通过时间序列模型和机器学习算法，实现对人流量的预测，并制作了可视化查询页面。这样就可以直观地检测各个站点和线路的人数，及时对大客流情况作出预警。

* 点评：依托SODA给出的数据进行了比较实在的分析、处理、和可视化。故事比较清晰。

[决赛视频](https://mp.weixin.qq.com/s?__biz=MzA5NjE1ODU1MQ==&mid=2649498924&idx=2&sn=7e5e32be153e46b4f3ad54e66a803b3a&chksm=88acd314bfdb5a0262381a690103b55b4d207aee6b0a7a7811cb88a33a4002478e8c9af62d84&scene=0&key=126df665731994ec72c2844b29473b9b22b06fce63c2a60f8a9498a043de1d9a67a2a06010de4037167aa43fb40ec73d54ff55ac7e7083b59346cbbd80fd5701dfb4b1fc981ba2c2a4a85117df3c6736&ascene=0&uin=MTM0NDQxNjYwMA%3D%3D)

![地铁图](https://mmbiz.qpic.cn/mmbiz_gif/bMX5EkeMvZ0SIMvzWLibs628adzMYxQrkWjZ975v6ickGQAzQFrwyTCY8OtEBibM6WMrlgOAprP1swI6DZ08z1ftQ/0?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

![人流变化](https://mmbiz.qpic.cn/mmbiz_png/bMX5EkeMvZ0SIMvzWLibs628adzMYxQrkxMpYpicC1INf2tRzVOfZMXxwP3WFnU2VCon3J1iahQavcgaAWZkIlGpA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1)

<a name="e图商圈"></a>

##e图商圈

* 队伍：比特猎人

* 摘要：聚焦商圈安全和食品安全，提出基于用户喜好、商铺流量、食品安全综合考量的商圈内店铺推荐模型及购物路线生成策略，最终产品为移动APP

* 实现方法：系统通过交叉分析多个维度的大数据，针对消费者不同的购物偏好、商圈热度以及客户流量，给他们推荐不同的逛街路线，从而做到人群分流，实现“导购驱动导流”。在实际操作中，比特猎人用到了上面提到的SODA开放的10个数据库，包括商圈客流数据、联通用户信息、用户电信类标签、餐饮检查数据、强生出租车数据、公交卡数据、气象数据等等。融合了交通卡、出租车、商圈、气象、地理位置等诸多数据后，比特猎人设计了一套独特的流量预测算法。所有店铺都会有一个流量信息，当流量达到一定程度时，系统会停止推荐，以防安全隐患。当你下次再逛商场时，这个App不仅知道你喜欢什么店铺，还能告诉你什么时间逛、怎么逛用户体验最佳。

* 点评：中规中矩，数据维度多，但是目测数据量不足以支撑出有意义的分析结果。

[决赛视频](https://mp.weixin.qq.com/s?__biz=MzA5NjE1ODU1MQ==&mid=2649498964&idx=2&sn=95ff565c1a24ff729d51e11c6158ad8e&chksm=88acd36cbfdb5a7abbc75c2de67579f7e84e013ce07cefcaae78e1ddda8fde67330362f5b668&scene=0&key=4bbfc5e76b8603bd4759ce50243eeb6f0f3475df4c8d612471d2558acf67127a87dc20a74026078df420e151bdd5bd80d2c9affab4663ac51f08e24fa68959d68e2430bb0ed4c69abadf85d62798b013&ascene=0&uin=MTM0NDQxNjYwMA%3D%3D)

![商圈图](https://mmbiz.qpic.cn/mmbiz_jpg/BtLdpzJd1K0sQRFb8X9pMVOxaxO6OTGcxF8qYBib7XZS33wnH9sPHicuQCpibJGgC8R8IH744zePtrWZsHlcoJXxw/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1)



<a name="环境安全可视分析系统"></a>

##环境安全可视分析系统

* 摘要：从环境、交通、治安、视频、人流五个方面，为人们租房、买房、商业投资等决策行为提供安全方面的综合分析服务。

* 实现方法：使用的环境数据，包括中国天气网的天气数据、环保局的企业监测站点数据以及上海一家非政府环保组织——青悦提供的污染监测数据。项目组将这些环境相关数据集，与地理位置数据、城市GDP数据等其他数据进行交叉分析，为用户提供环境信息服务。为了更直观地让用户知晓自己正身处一个怎样的环境，团队结合用户GPS定位、实时风向数据及污染企业地理位置信息制作出一个可视化界面，将用户所处的“污染环境”还原出来。

* 点评：环境安全问题热点抓的不错。可视化有特色，大小图追溯方式值得借鉴。

[决赛视频](https://mp.weixin.qq.com/s?__biz=MzA5NjE1ODU1MQ==&mid=2649498924&idx=2&sn=7e5e32be153e46b4f3ad54e66a803b3a&chksm=88acd314bfdb5a0262381a690103b55b4d207aee6b0a7a7811cb88a33a4002478e8c9af62d84&scene=0&key=1c1f454375e2a3ada6f4dc672e022e2e9cefd9b2908ce1c65aa3a04f212d97eabf18d2023d4842205dc1474cc20f5b54ac578e575604d2155251563b7931f2764c09c6e282693fa2e8b4a5168ad2d5db&ascene=0&uin=MTM0NDQxNjYwMA%3D%3D)

![污染图](https://mmbiz.qpic.cn/mmbiz_gif/bMX5EkeMvZ35mxYnzEgaZo0RJjHo6u0q5qwGT0j0jSk2ETB2lUAU9J8LgxNLAoXKhyYtGCJclFZ7qVyYW9VwuQ/0?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

![城市污染图](https://mmbiz.qpic.cn/mmbiz_gif/bMX5EkeMvZ35mxYnzEgaZo0RJjHo6u0qKrxf63M2Gl7KuGicxAZZvlbhT5F5B5czlGFrA7IPicr5JEuVOctrIsxw/0?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

![工厂污染情况概览-细节](https://mmbiz.qpic.cn/mmbiz_gif/bMX5EkeMvZ35mxYnzEgaZo0RJjHo6u0qcrn9EtApia4iaygPwGI0k6MbaHoLFebwgQ5xAN1YfXibhyicQIRXkWZib4w/0?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)



<a name="评安食客"></a>

##评安食客

* 队伍：吃货俱乐部

* 摘要：一款利用用户评论、天启、食品检测等数据，针对食品安全问题，满足政府的监察监管、食客的获取安全食品保障与商家彰显信用价值需求的一体化解决方案。

* 实现方法：“吃货俱乐部”主要采用了情感分析的方法对数据进行了分析和处理。作为一种特殊的数据类型，计算机是无法主动识别文本数据的。团队首先使用深度学习的算法将文本数据转化成了数值向量，同时还包括了文字之间的信息。这个转化过程主要通过一个三层的神经网络来完成。在计算词语的频率时，优化采用了Huffman编码，有效降低了计算的复杂度，使大规模的文本分析变得更加高效。接下来，他们使用了无监督机器学习的方法对文本进行了词语聚类。然后根据词类的群体特征，主要将这些词分为了环境（地理位置、地铁、闹市区等）、卫生（服务员、盘在、木筷等）、综合（服务、口味等）三大类。以此为基础，他们再对文本进行了情感分析，将不同的情感进行打分。

* 点评：食品安全切入点不错，天气数据可以说是强行揉进来了。如果能够结合食品供应链的数据，效果会上一个台阶。

[决赛视频](https://mp.weixin.qq.com/s?__biz=MzA5NjE1ODU1MQ==&mid=2649498967&idx=1&sn=6bf42fbb1ea723e4241d89613a2ff238&chksm=88acd36fbfdb5a79578c1ba3e075963e254333446a13b35c31cf20106b67dc1a51fcb320c67e&scene=0&key=27e59116b734781c0ad405259e0383ccf9b8bf21106e291f065f05f733dfd4abdcf7556891dca94b5cfd4900724620b399b65533615339cf4b9793172c36643bfddb2e85c750c791365a8d8e4939c034&ascene=0&uin=MTM0NDQxNjYwMA%3D%3D)

![词云](https://mmbiz.qpic.cn/mmbiz_jpg/bMX5EkeMvZ29IB6QOcUaBhIqEibhbVADtGk4lrodM4uwRnbXPTNAibVBvD4Zdw5VJY6nI4EkoXOibByozsA2uh2Vw/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1)

![排名](https://mmbiz.qpic.cn/mmbiz_png/bMX5EkeMvZ29IB6QOcUaBhIqEibhbVADtDwAmDb3o90xsGgUNibwj7Nic8licHmaNTOa2GD51ibfOWdj0kqjMb8FGoA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1)



<a name="智慧防霾"></a>

##智慧防霾

* 摘要：通过自主研发的智能评估系统和智能口罩，使用户可以更高效、准确的保护生命安全，减少呼吸系统疾病与死亡率。

* 实现方法：除了机器学习，还使用了土地利用回归模型（Land Use Regression）。这种模型可以用来研究多种因素影响下空气污染物的暴露浓度及空间分布情况。在公共健康、空气质量管理以及城市规划等领域都有应用。在这个模型中，涉及的影响因素包括空间上的距离、密度、土地利用、人口统计特征和地形特征等等。而本次SODA大赛正是开放了这些数据中的一部分，SUSMART GROUP尝试用这些开放的数据集，来建立一套更加高效的防霾方法。他们用到的大量政府开放数据中，包含气象数据（风速、风向、湿度、降雨量等）、基于联通基站数据判断的人口数据、上海规划局提供的用地数据和部分交通数据，当然也包括了PM2.5站点监测数据和环境监测中心提供的空气质量数据。

* 点评：出发点很好，有产品规划。目前缺少出行GPS数据，如果能够结合摩拜单车GPS，可以形成一个更好的防雾霾方案。

[决赛视频](https://mp.weixin.qq.com/s?__biz=MzA5NjE1ODU1MQ==&mid=2649498968&idx=1&sn=4e62e98c83e89718c325bc0b74cf1a17&chksm=88acd360bfdb5a7647bea1f59da5fabe175b1646251150c94502b947cb0d5f41b60d1b27ed8f&scene=0&key=4bbfc5e76b8603bd7a61b10e2c401b1ea60727333b9cf6a78a4bcc2cb66d5a30ae703788410bc8b2fa7fac08c768d18656f392223bedc873a509306a936f55db7157eca6d8d9b1a7d015b8975957cecc&ascene=0&uin=MTM0NDQxNjYwMA%3D%3D)

![pm25](https://mmbiz.qpic.cn/mmbiz_png/bMX5EkeMvZ2dzjbTooYDucvxTsGaj1pNNz8utfTURlibGrAn2jJy9Fic7FxRGDGsjKEAfo3oxsrzE0dAGFONck2w/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1)

![app](https://mmbiz.qpic.cn/mmbiz_png/bMX5EkeMvZ2dzjbTooYDucvxTsGaj1pNPcPa1fuBVZ9agHdynE3xnnQDzh1UQekp55ADp4BGiagn8aWicIXlNfpg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1)


<a name="changify"></a>

##Changify

* 摘要：一套结合自顶向下的城市监控与投诉，和自底向上的市民众包城市问题，帮助城市完善治理，及时响应城市问题的数字化平台。该项目已在英国Plymouth等城市试点，目前有神州数码等合作方共同计划落地中国。

* 实现方法：D4SC将Changify设计成了一款使用API接口的应用程式，通过这个接口，微信、微博、脸书等社交媒体用户就能够通过登录传统社交网络，连接Changify的服务了。当用户拍摄上传照片时，需要开启地理信息验证服务，只有在被认证地理位置拍摄的照片才会被系统上传到社群。照片上传后，如果某些用户上传的照片常常被大家认为有用，并解决了一些城市街道的实际问题，那么这些用户在社群中的声誉就会变好，他们的照片就会有更高的推荐级别。

* 点评：已经开始成型的产品，众包的公众参与是特色和亮点，可以关注其后续发展。

[决赛视频](https://mp.weixin.qq.com/s?__biz=MzA5NjE1ODU1MQ==&mid=2649498969&idx=1&sn=8fdbe8b57efd516ca6142fa20e565ca3&chksm=88acd361bfdb5a7723656c31a804168534e061c3933a7bab4f4439691e32572af1d7aedcc01c&scene=0&key=fbf9e68652914f98292e95ca0a7b18c75574e1a25cf3a702c975a7173d0d75c871fb7c637976e012575aa0719945dab1ca042ea368452c65fede0b6a0718a1308ca24bbbace8ce8431675e9b312ffbe8&ascene=0&uin=MTM0NDQxNjYwMA%3D%3D)

![app](https://mmbiz.qpic.cn/mmbiz_gif/bMX5EkeMvZ11yodibo9uicdl88Xa9wNV7vRsNeRoFE6Kb2lQAZ6fHomjGrotTh9b3BTxBJia14PlM5VLCpMQHmSWA/0?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

![视频分析](https://mmbiz.qpic.cn/mmbiz_gif/bMX5EkeMvZ11yodibo9uicdl88Xa9wNV7vOnQ8j7TefWUhTOCF1mw4OibSGwvewmt7gh3uiaLiarpBbLcxiatIISUZGA/0?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)
 


<a name="优尼克unique：智能感知城市安全宜居服务系统"></a>

##优尼克(Unique)：智能感知城市安全宜居服务系统

* 提供城市监控、突发预警、资源调派等服务，为管理者提供更好的决策辅助支持。我们提供智能感知、智能推送、宜居评估等服务，通过信息透明化让居住者拥有更好的居住环境知晓力。

* 实现：通过21个维度的城市大数据、7个基本信息标签和5个城市分析角度等，将上海这座城市的各类民生安全相关的信息，都掠影浓缩在了一整张交互式的地图里，打造了一个上海的“城市安全宜居服务系统”。

* 点评：来融资的，没讲产品细节，没有实际的内容。

[决赛视频](https://mp.weixin.qq.com/s?__biz=MzA5NjE1ODU1MQ==&mid=2649498970&idx=1&sn=64765526953bf2671e90949d0ee1d669&chksm=88acd362bfdb5a74396b97c5e8c78211f58fc4a448d2079f7a51fc105740988272625cdaae71&scene=0&key=82376c78f05b5544cd203c5a71f7cbd5a6850ca7056b170b3e64d32b75244f57bcfe7aa286b8b8de8da69de081ea415d2da3d4107be27bd069d88cd3724c82617941a048ce40decc3a1bfddbaf82e544&ascene=0&uin=MTM0NDQxNjYwMA%3D%3D)
