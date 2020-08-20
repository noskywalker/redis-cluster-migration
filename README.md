![] (logo.png)
## redis集群间数据迁移，纯bash实现方案，简单轻量，复用度高

#### 1、自动识别类型，不用写策略模式了
#### 2、scan扫描，规避集群block风险
#### 3、自动forward到正确的分片
#### 4、自定义key，支持部分搬迁也支持整体搬迁

## 用法

````bash
#替换模式，如果目标集群已存在则替换
sh redis.sh [replace]
````
###
````bash
# add模式，如果目标集群已存在则skip
sh redis.sh
````

## 配置说明
#### key配置
````bash
#多个key，空格分隔，模糊匹配
keys="yingApi* fortune* *testKey*"

````
#### redis来源集群配置
````bash
#来源节点，支持单点和集群，空格分隔
src_cluster_nodes="10.141.17.68:6379 10.141.17.68:6389"
src_cluster_passwd="redisclusternew"
````

#### redis目标集群配置

````bash
dest_cluster_nodes="10.141.19.36:6379 10.141.19.36:6389 10.141.19.36:6399"
dest_cluster_passwd="perftest"
````

## 不足
##### 写的时候想多了，其实原生的-c move性能应该更高，而我是手工move到节点，可以改造一下

## todo
##### 根据任务及集群数量自动支持多线程跑，提高性能
