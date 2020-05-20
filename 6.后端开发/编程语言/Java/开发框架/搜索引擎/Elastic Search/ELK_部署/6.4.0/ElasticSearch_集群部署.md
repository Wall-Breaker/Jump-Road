#ElasticSearch_集群部署


* 步骤
1. 安装ES
    * 官网
    * 下载解压即可
2. 配置ES
以三个节点举例（192.168.137.7、192.168.137.8、192.168.137.9）
* 192.168.137.7
```
cluster.name: es-cluster

node.name: node-1
node.master: true
node.data: true

network.host: 192.168.137.7

http.port: 9200

discovery.zen.ping.unicast.hosts: ["192.168.137.7","192.168.137.8","192.168.137.9"]
discovery.zen.minimum_master_nodes: 2

#为ElasticSearch-head配置
http.cors.enabled: true
http.cors.allow-origin: "*"
```
* 192.168.137.8
```
cluster.name: es-cluster

node.name: node-2
node.master: true
node.data: true

network.host: 192.168.137.8

http.port: 9200

discovery.zen.ping.unicast.hosts: ["192.168.137.7","192.168.137.8","192.168.137.9"]
discovery.zen.minimum_master_nodes: 2

#为ElasticSearch-head配置
http.cors.enabled: true
http.cors.allow-origin: "*"
```
* 192.168.137.9
```
cluster.name: es-cluster

node.name: node-3
node.master: true
node.data: true

network.host: 192.168.137.9

http.port: 9200

discovery.zen.ping.unicast.hosts: ["192.168.137.7","192.168.137.8","192.168.137.9"]
discovery.zen.minimum_master_nodes: 2

#为ElasticSearch-head配置
http.cors.enabled: true
http.cors.allow-origin: "*"
```
3. 运行ES
















* 参考资料
---
#ElasticSearch6.4.0集群搭建
https://blog.csdn.net/qq_29167297/article/details/92639779