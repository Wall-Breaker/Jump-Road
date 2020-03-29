#Elastic Search_常用API_RESTful版

索引操作
---

* 创建非结构化索引
``` 
PUT http://localhost:9200/test
{
   "settings": {
      "index": {
         "number_of_shards": "2", #分片数
         "number_of_replicas": "0" #副本数
      }
   }
}
```

* 删除索引
``` 
DELETE http://localhost:9200/test
{
   "acknowledged": true
}
``` 

* 查询索引信息
``` 
GET http://localhost:9200/test/_settings
```

* 查询索引映射
```
GET http://localhost:9200/testIndex/_mapping
```
 
* 动态修改分片
``` 
PUT http://localhost:9200/test/_settings
{
    "number_of_replicas": 1
}
```

* Elasticsearch插入、修改字段
``` 
PUT http://localhost:9200/test/_mapping/doc
{
  "properties": {
    "test789": {
      "type": "geo_shape",
      "ignore_z_value": true
    }
  }
}
``` 
>[【参考】Elasticsearch插入、修改字段](https://www.cnblogs.com/hcy-fly/p/8602463.html)


别名
---
* 增加
``` 
POST /_aliases
  {
      "actions" : [
          { "add" : { "index" : "test1", "alias" : "alias1" } }
      ]
  }
``` 
* 删除
``` 
  POST /_aliases
    {
        "actions" : [
            { "remove" : { "index" : "test1", "alias" : "alias1" } }
        ]
    }
``` 
* 修改  
``` 
    POST /_aliases
    {
        "actions" : [
            { "remove" : { "index" : "test1", "alias" : "alias1" } },
            { "add" : { "index" : "test2", "alias" : "alias1" } }
        ]
    }
``` 
* 查询
``` 
    GET test1/_alias/*
``` 

文档数据操作
---

* 查询所有索引所有字段
```
GET _search
{
  "query": {
    "match_all": {}
  }
}
```

* 查询一个索引所有字段
```
GET /testIndex/doc/_search
{
  "query": {
    "match_all": {}
  }
}
```

* 查询一个索引一个字段
```
GET /testIndex/doc/_search
{
  "query": {
    "match": {
        "testField":"testText"
    }
  }
}
```

* 设置查询结果数量
```
GET /testIndex/doc/_search?size=50 
```


* 分页查询
```
GET /testIndex/doc/_search
{
"query":{
        "match":{"name":"张三"}
    },
"from":0,
"size":20
}
```


聚合查询
---
* 根据某一字段分组聚合统计数量
```
POST /testIndex/doc/_search?size=0
{
  "aggs": {
    "age_terms": {
      "terms": {
        "field": "testField",
        "size": 15
      }
    }
  }
}
```
>"doc_count_error_upper_bound": 0：文档计数的最大偏差值  
>"sum_other_doc_count": 463：未返回的其他项的文档数  
>[【参考】聚合分析](https://www.cnblogs.com/leeSmall/p/9215909.html)

* 根据某一字段按时间分组
```
POST /testIndex/doc/_search?size=0
{
  "aggs": {
    "groupDate": {
      "date_histogram": {
        "field": "testField",
        "interval": "month",
        "format": "yyyy-MM"
      }
    }
  }
}
```
> [【参考】时间聚合查询](https://blog.csdn.net/jianshaoguang8886/article/details/82178817
)


其它
---

* 拼音分词测试
```
POST _analyze
{
"analyzer":"pinyin",
"text":"波波网吧"
}
```

* 修改es中所有的index的最大返回结果数量（默认为10000）
```
PUT _all/_settings
{
  "index":{
    "max_result_window": 1000000000
    
  }
}
```

* 修改es中一个index的最大返回结果数量（默认为10000）
```
PUT /testIndex/_settings
{
  "index":{
    "max_result_window": 1000000000
    
  }
}
```
> [查找10000条数据之后的数据](https://blog.csdn.net/Misaki_root/article/details/101203647?depth_1-utm_source=distribute.pc_relevant.none-task)
> [Elasticsearch 查询10000条限制与totalhits值最大10000的解决](https://blog.csdn.net/weixin_43876919/article/details/103292463?depth_1-utm_source=distribute.pc_relevant.none-task&utm_source=distribute.pc_relevant.none-task)


