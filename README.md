# Kubernetes-dep-mysql-cluster

#### 项目说明
旨在使用k8s部署mysql集群，能够做到主从同步，读写分离，以及当节点出现故障的时候自动生成新的节点。

#### 环境准备

nfs服务器：192.168.20.101：
    /data/nfs-share/mysql-cluster/data-0
    /data/nfs-share/mysql-cluster/data-1
    /data/nfs-share/mysql-cluster/data-2

#### 创建pv资源

kubectl apply -f pv.yaml

#### 创建cm，也就是为不同的mysql服务器配置不同的配置文件

kubectl apply -f mysql-configmap.yaml

#### 创建service资源，其中主也就是写服务器是无头服务，而从也就是读服务器是正常暴露服务

kubectl apply -f mysql-service.yaml

#### 创建statefulset-mysql资源

kubectl apply -f mysql-statefulset.yaml
