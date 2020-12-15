#Redis_入门教程

##一、Redis简介
1. key-value的nosql产品，类似Memcached，数据都缓存在内存中。
2. 存储的value类型较后者跟丰富，包括string(字符串)、list（链表）、set（集合）、zset（有序集合）、hash
3. 相较于后者，redis会周期性的把内存中的数据写入硬盘（俗称数据持久化）
4. 由于redis支持类型众多，也被称为结构化的nosql数据库

##二、nosql简介
1. 常见nosql产品
    1. redis
    2. mongodb
    3. memcache
2. nosql产品特点
    1. 一般不使用严格的表结构
    2. 查询一般不使用sql查询
3. 常见的nosql产品比较
    1. kv存储
        1. 代表：redis、memcached
        2. 简介：使用key快速查value，memcached支持string类型的value，redis支持string、hash、set、zset、list
    2. 文档存储
        1. 代表：MongoDB、CouchDB
        2. 简介：使用JSON或类JSON的BSON数据结构，存储内容为文档型，能实现部分关系数据库的功能
    3. 列存储
        1. 代表：HBase、Cassandra
        2. 简介：按照列进行数据存储，便于存储结构化和半结构化数据，方便做数据压缩和针对某一列和某几列的数据查询
    4. 图存储
        1. 代表：Neo4J、FlockDB
        2. 简介：图形关系的存储，可很好弥补关系数据库在图形存储的不足
    5. 对象存储
        1. 代表：Db4o、Versant
        2. 简介：通过类似面向对象语言的方式操作数据库，通过对象的方式存取数据
    6. XML数据库
        1. 代表：Berkeley DB XML、BaseX
        2. 简介：高效存储XML数据，支持XML的内部查询语法，如XQuery，XPath

##三、redis的安装
1. windows的安装
    1. 注意事项
        1. 非中文非空格目录下安装
        2. 启动redis服务需要在windows命令行下进行，并且要以超级管理员身份
2. linux的安装
        