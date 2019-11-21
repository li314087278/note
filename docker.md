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
sudo systemctl start docker
~~~

### 设置开机启动

~~~
sudo systemctl enable docker
~~~
