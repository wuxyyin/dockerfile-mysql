# 基于CENTOS:7构建MYSQL5.5.23镜像

## 简介
 * 本镜像基于CentOS7和MYSQL5.5.23源码进行构建

## tags列表
 * 5.5.23(CentOS:7/Dockerfile)
 * 

## 启动mysql容器
    $ docker run -dit --restart=always --name some-mysql registry.qishon.com/mysql:tag
    
    some-mysql是你想给当前容器起的名字，tag是mysql的tag标签

## 从其他容器中的应用连接mysql
    $ docker run -dit --link some-mysql:mysql --name some-app application-that-uses-mysql:tag

## 指定使用宿主机的端口
    $ docker run -dit --restart=always -p 宿主机端口:3306 --name some-mysql registry.qishon.com/mysql:tag

## 指定使用宿主机的目录
    $ docker run -dit --restart=always -v 宿主机目录:/data/mysql --name some-mysql registry.qishon.com/mysql:tag

## 默认创建数据库
    $ docker run -dit --restart=always -e MYSQL_DATABASE=some-database --name some-mysql registry.qishon.com/mysql:tag
    
## 默认创建数据库用户
    $ docker run -dit --restart=always -e MYSQL_USER=some-user -e MYSQL_PASSWORD=some-pwd --name some-mysql registry.qishon.com/mysql:tag

## 环境变量
 * MYSQL_DATABASE
 
        容器启动的时候默认创建的数据库，如果不传入此参数默认创建名称为qishon的数据库，此数据库会授权给MYSQL_USER,MYSQL_PASSWORD（参照下一项）
 * MYSQL_USER,MYSQL_PASSWORD

        容器启动的时候默认创建的用户，默认用户：qishon，默认密码：qishon
 * MYSQL_ROOT_PASSWORD
  
        数据库root用户的默认密码

