## docker

## 参考文档

>[https://docs.docker.com/install/linux/docker-ce/centos/](https://docs.docker.com/install/linux/docker-ce/centos/)

## 安装docker

### 卸载旧版本

~~~
$ sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
~~~


### 设置仓库

~~~
$ sudo yum install -y yum-utils \
  device-mapper-persistent-data \
  lvm2
~~~

~~~
$ sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
~~~

### 安装docker引擎

~~~
$ sudo yum install docker-ce docker-ce-cli containerd.io
~~~

### 启动docker

~~~
$ sudo systemctl start docker
~~~

### 设置开机启动

~~~
$ sudo systemctl enable docker
~~~

## 运行容器

### portainer dockerui 

docker可视化管理

~~~

$ docker pull docker.io/portainer/portainer


$ docker run -d -p 9000:9000 --restart=always -v /var/run/docker.sock:/var/run/docker.sock --name portainer portainer/portainer

~~~

### centos7

~~~

$ docker pull centos:7


$ docker run --privileged -d -p 7722:22 -p 7780:80 --name=centos7 centos:7 /usr/sbin/init
~~~

进入bash

~~~

$ docker exec -it centos7 /bin/bash
~~~


### jenkins 


~~~

$ docker pull jenkins/jenkins:lts 


$ docker run -p 8084:8080 -p 50000:50000 --restart=always jenkins

~~~


### cms

织梦cms

~~~

$ docker pull chengxulvtu/dedecms:utf8_full_5.7


$ docker run -d -p 8099:80 --restart=always -name dedecms  -v /root/webroot/dedecms:/var/www/html chengxulvtu/dedecms:utf8_full_5.7

~~~




### mysql


~~~

$ docker pull mysql:5.6


$ docker run -p 3306:3306 --restart=always --name mysql -v /root/mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=root -d mysql:5.6

~~~



### zookeeker


~~~

$ docker pull zookeeper:3.4


$ docker run -p 2181:2181 --name zookeeper --restart always -d -v /root/zookeeper/:/conf/ zookeeper:3.4

~~~


### redis


~~~

$ docker pull redis


$ docker run -p 6379:6379 -d --restart=always --name redis redis

~~~


### elasticsearch

~~~

$ docker pull elasticsearch:7.4.2


$ docker run -d --name elasticsearch -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" elasticsearch:7.4.2

~~~


