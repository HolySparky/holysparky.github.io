---
title: JSON转CSV过程中要注意的坑
tags: 
notebook: INESA
layout: post
category: tech,python,json,csv,data
author: "Pengfei Zhang"
---

在把食品溯源数据导入统一数据平台CKAN的过程中，我们希望将原来存储在MongoDB中的JSON格式数据转化成列表的CSV，一方面可以减少文件的大小，另一方面表格的方式也方便在CKAN上进行查看和进一步下载处理。

不过，在实际转换时，需要注意以下一些可能出现问题的地方：

## JSON格式问题

JSON格式本身如果缺／多元素，或者格式不正确，将直接导致JSON读取失败，这一点 stackoverflow上已经有很多踩坑的经验了，这里不再赘述。总的来说，当你使用 `json.loads()` 进行读取的时候，如果系统扔出来 `ValueError`异常，第一步恐怕就是需要看看这个json是不是规范的格式。



## JSON文件包含多元素问题

Python中，使用 json.load 可以将文件读入成json结构，但是需要注意的是，其默认一个文件是一个json，而我们使用mongo-export导出的json文件中则包含了多个json对象，如下：


    { "_id" : { "$oid" : "586692e1208a6f78a40987b6" }, "tag_id" : "586692e1208a6f78a40987b5", "tag_sn" : "586692e1208a6f78a40987b5", "tag_sn_producer_code" : "SHFDA", "enterprise_id" : 782, "product_id" : 44900, "process_id" : 106, "is_downstream" : false, "data_type" : "catering", "data_node_type" : "in", "data_date" : "2016-12-30", "data_batch" : "platform-batch_e-782_accountdata_20161230_上海肯德基有限公司成山餐厅_餐饮_20161230.xls", "nodes" : { "production" : { "parameters" : { "producerName" : "中粮东海粮油工业（张家港）有限公司", "batch" : "2016-12-18", "productionDate" : "2016-12-18" } }, "purchase" : { "parameters" : { "vendorTel" : "010-85018668", "unit" : "箱", "vendorName" : "中粮国际（北京）有限公司上海分公司", "purchaseDate" : "2016-12-30", "vendorAddr" : "上海市中山南二路440号301室", "quantity" : "1" } } }, "status" : 1, "created_by" : "admin@SHA240", "created_on" : 1483117281, "updated_by" : "admin@SHA240", "updated_on" : 1483117281 }
    { "_id" : { "$oid" : "586692e1208a6f78a40987b8" }, "tag_id" : "586692e1208a6f78a40987b7", "tag_sn" : "586692e1208a6f78a40987b7", "tag_sn_producer_code" : "SHFDA", "enterprise_id" : 782, "product_id" : 8696, "process_id" : 106, "is_downstream" : false, "data_type" : "catering", "data_node_type" : "in", "data_date" : "2016-12-30", "data_batch" : "platform-batch_e-782_accountdata_20161230_上海肯德基有限公司成山餐厅_餐饮_20161230.xls", "nodes" : { "production" : { "parameters" : { "producerName" : "上海亚太国际蔬菜有限公司", "batch" : "2016-12-29", "productionDate" : "2016-12-29" } }, "purchase" : { "parameters" : { "vendorTel" : "021-54592133*1100", "unit" : "袋", "vendorName" : "上海亚太国际蔬菜有限公司", "purchaseDate" : "2016-12-30", "vendorAddr" : "上海市金山区廊下镇漕廊公路7395号", "quantity" : "1" } } }, "status" : 1, "created_by" : "admin@SHA240", "created_on" : 1483117281, "updated_by" : "admin@SHA240", "updated_on" : 1483117281 }
    { "_id" : { "$oid" : "586692e1208a6f78a40987ba" }, "tag_id" : "586692e1208a6f78a40987b9", "tag_sn" : "586692e1208a6f78a40987b9", "tag_sn_producer_code" : "SHFDA", "enterprise_id" : 782, "product_id" : 8697, "process_id" : 106, "is_downstream" : false, "data_type" : "catering", "data_node_type" : "in", "data_date" : "2016-12-30", "data_batch" : "platform-batch_e-782_accountdata_20161230_上海肯德基有限公司成山餐厅_餐饮_20161230.xls", "nodes" : { "production" : { "parameters" : { "producerName" : "上海亚太国际蔬菜有限公司", "batch" : "2016-12-29", "productionDate" : "2016-12-29" } }, "purchase" : { "parameters" : { "vendorTel" : "021-54592133*1100", "unit" : "袋", "vendorName" : "上海亚太国际蔬菜有限公司", "purchaseDate" : "2016-12-30", "vendorAddr" : "上海市金山区廊下镇漕廊公路7395号", "quantity" : "3" } } }, "status" : 1, "created_by" : "admin@SHA240", "created_on" : 1483117281, "updated_by" : "admin@SHA240", "updated_on" : 1483117281 }


对于这种情况，需要在load文件的时候逐行读入，如：


        raw_data=[]
        with open(json_file_path) as f:
            for line in f:
                raw_data.append(json.loads(line))



## 编码问题

在使用json模块的时候需要注意的是对中文的处理，loads方法如果传入的字符串的编码不是UTF-8的话,需要用encoding指定字符编码:



    def to_string(s):
        try:
            return str(s)
        except:
            #Change the encoding type if needed
            return s.encode('utf-8')



## json-csv 转换代码


    import json
    import csv

    ##
    # Convert to string keeping encoding in mind...
    ##
    def to_string(s):
        try:
            return str(s)
        except:
            #Change the encoding type if needed
            return s.encode('utf-8')

    def reduce_item(key, value):
        global reduced_item

        #Reduction Condition 1
        if type(value) is list:
            i=0
            for sub_item in value:
                reduce_item(key+'_'+to_string(i), sub_item)
                i=i+1

        #Reduction Condition 2
        elif type(value) is dict:
            sub_keys = value.keys()
            for sub_key in sub_keys:
                reduce_item(key+'_'+to_string(sub_key), value[sub_key])

        #Base Condition
        else:
            reduced_item[to_string(key)] = to_string(value)


    if __name__ == "__main__":
        if len(sys.argv) != 4:
            print "\nUsage: python json_to_csv.py <node_name> <json_in_file_path> <csv_out_file_path>\n"
        else:
            #Reading arguments
            node = sys.argv[1]
            json_file_path = sys.argv[2]
            csv_file_path = sys.argv[3]

        raw_data=[]
        with open(json_file_path) as f:
            for line in f:
                raw_data.append(json.loads(line))


            #fp = open(json_file_path, 'r')
            #json_value = fp.read()
            #raw_data = json.loads(json_value)

            try:
                data_to_be_processed = raw_data[node]
            except:
                data_to_be_processed = raw_data

            processed_data = []
            header = []
            for item in data_to_be_processed:
                reduced_item = {}
                reduce_item(node, item)

                header += reduced_item.keys()

                processed_data.append(reduced_item)

            header = list(set(header))
            header.sort()

            with open(csv_file_path, 'wb+') as f:
                writer = csv.DictWriter(f, header, quoting=csv.QUOTE_ALL)
                writer.writeheader()
                for row in processed_data:
                    writer.writerow(row)

            print "Just completed writing csv file with %d columns" % len(header)


