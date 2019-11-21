### 安装jenkins

~~~
wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo

rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key

yum install jenkins
~~~


### 查看安装目录
~~~
rpm -ql jenkins
~~~

~~~
/var/lib/jenkins/

~~~

### 安装jdk
~~~
yum install java -y
~~~

### 设置path
~~~
export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.181-3.b13.el7_5.x86_64
export JRE_HOME=$JAVA_HOME/jre
export CLASSPATH=$JAVA_HOME/lib:$JRE_HOME/lib:$CLASSPATH
export PATH=$JAVA_HOME/bin:$JRE_HOME/bin:$PATH
~~~


### 让配置生效
~~~
source  /etc/profile
~~~

### nginx 代理

~~~
location /jenkins/ {
 
      proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
      proxy_set_header Host $http_host;
      proxy_pass http://127.0.0.1:8084;
   }
~~~

/etc/sysconfig/jenkins

~~~

JENKINS_ARGS=" --prefix=/jenkins"
~~~


### 启动

~~~
systemctl status jenkins
systemctl start jenkins
~~~
