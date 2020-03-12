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

* 动态修改分片
``` 
PUT http://localhost:9200/test/_settings
{
    "number_of_replicas": 1
}
``` 

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
