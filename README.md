![image](logo.png)
## migrate data from stand-alone redis to redis cluster.Implemented by bash only

#### 1、Can recoginize data type automatically
#### 2、Using scan to avoid cluster blocking inadequacies
#### 3、Be able to forward to the specific sharding of cluster


## how to use

````bash
#write replace mode
sh redis.sh [replace]
````
###
````bash
# add mode，if key exists then skip
sh redis.sh
````

## 配置说明
#### the specific keys that you want to migrate to new cluster
````bash
#the key should be migrated
keys="yingApi* fortune* *testKey*"

````
#### the original redis node that you want to migrate from
````bash
#The source that should migrate,suppprting multiple nodes
src_cluster_nodes="10.141.17.68:6379 10.141.17.68:6389"
src_cluster_passwd="redisclusternew"
````

#### desitination redis cluster that you want to migrate to

````bash
dest_cluster_nodes="10.141.19.36:6379 10.141.19.36:6389 10.141.19.36:6399"
dest_cluster_passwd="perftest"
````
