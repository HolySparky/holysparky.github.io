---
title: 数据服务平台门户与数据治理工具对接文档
tags: data,ckan
notebook: SJTU
layout: post
category: tech
author: "Pengfei Zhang"
---

*撰写人：张鹏飞*

在数据服务平台中，我们采用基于开源的CKAN开发的数据集管理与门户展示，采用随巢作为后台的数据治理工具，本文档讨论两者的对接关系及接口API。

 
![ckan-suichao](https://github.com/ZionPF/Pictures/blob/master/SJTU/ckan_suichao.png?raw=true)

如上图，数据的流通过程如下：

1. 随巢负责从数据湖（HDFS）中读取数据，进行治理
2. 将治理好的数据存储到HDFS中成为输出文件。
3. 随巢调用CKAN的API，将文件连同数据的描述信息（metadata）上传至CKAN成为数据集
4. CKAN接受API调用后，将数据集加入自身数据结构中，并将文件转存至自身管理的FileStore 相应路径下。
5. CKAN在后台自动或手动进行文件-数据库的拷贝，即将结构化文件转存到 Vertica 对应数据库中，方便在前端进行展示和简单的BI操作。
 


## CKAN 数据API

以开源的CKAN作为数据的前端门户的情况下，可以在CKAN中创建一个管理员账户，该账户具有数据上传的能力。

CKAN本身将数据文件存储在其 “FileStore” 中，可以使用  resource_create() 和 resource_update() API方法创建和上传数据集。

举例如下，使用curl创建并上传一个数据集：

    curl -H'Authorization: your-api-key' 'http://yourhost/api/action/resource_create' --form upload=@filetoupload --form package_id=my_dataset


类似的，使用Python进行API调用：

    import requests
    requests.post('http://0.0.0.0:5000/api/action/resource_create',
                  data={"package_id":"my_dataset"},
                  headers={"X-CKAN-API-Key": "21a47217-6d7b-49c5-88f9-72ebd5a4d4bb"},
                  files=[('upload', file('/path/to/file/to/upload.csv'))])

如果需要讲一个数据集中的某个文件更新成一个新的版本，可以使用 resource_update() 方法：

    curl -H'Authorization: your-api-key' 'http://yourhost/api/action/resource_update' --form upload=@newfiletoupload --form id=resourceid

类似的，可以使用  clear_upload 字段，将上传的文件更新成一个远端URL链接：

    curl -H'Authorization: your-api-key' 'http://yourhost/api/action/resource_update' --form url=http://expample.com --form clear_upload=true --form id=resourceid
