## 准备文件
 - pinpoint-collector-1.8.4.war：https://github.com/naver/pinpoint/releases/download/1.8.4/pinpoint-collector-1.8.4.war
 - apache-tomcat-9.0.24.tar.gz：http://archive.apache.org/dist/tomcat/tomcat-9/v9.0.24/bin/apache-tomcat-9.0.24.tar.gz
 - pinpoint-web-1.8.4.war：https://github.com/naver/pinpoint/releases/download/1.8.4/pinpoint-web-1.8.4.war
 - hbase-1.2.6.1-bin.tar.gz：http://archive.apache.org/dist/hbase/1.2.6.1/hbase-1.2.6.1-bin.tar.gz
 
将hbase-1.2.6.1-bin.tar.gz拷贝到pinpoint-hbase目录，将pinpoint-collector-1.8.4.war和apache-tomcat-9.0.24.tar.gz拷贝到pinpoint-collector目录，将pinpoint-web-1.8.4.war和apache-tomcat-9.0.24.tar.gz拷贝到pinpoint-web目录

## 制作镜像
  进入pinpoint-hbase目录，执行命令：
```
docker build -t zyz/pinpoint-hbase:1.8.4 .
```
  进入pinpoint-collector，执行命令：
```
docker build -t zyz/pinpoint-collector:1.8.4 .
```
  进入pinpoint-web，执行命令：
```
docker build -t zyz/pinpoint-web:1.8.4 .
```

## 创建并启动容器
  退回到pinpoint-docker目录，执行命令：
```
docker-compose up -d
```

## 说明
 - 本文hbase使用的是内置zookeeper，且端口2181并未暴露，但容器内是可以访问的
 - docker-compose.yml中的定义的pinpoint-hbase容器名称不能随意改动
