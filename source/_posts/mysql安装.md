---
title: mysql安装
date: 2021-06-15 17:24:27
---

## centos

### 卸载mariadb

    [root@localhost ~]# rpm -qa|grep mariadb
    [root@localhost ~]# rpm -e --nodeps mariadb-libs-5.5.56-2.el7.centos.x86_64

### 安装依赖

    [root@localhost ~]# yum -y install libaio
<!-- more -->
### 安装

    [root@localhost ~]# rpm -ivh mysql-community-common-5.7.22-1.el7.x86_64.rpm
    [root@localhost ~]# rpm -ivh mysql-community-libs-5.7.22-1.el7.x86_64.rpm
    [root@localhost ~]# rpm -ivh mysql-community-client-5.7.22-1.el7.x86_64.rpm
    [root@localhost ~]# rpm -ivh mysql-community-server-5.7.22-1.el7.x86_64.rpm

### 初始化

 - 初始化生成随机密码的root账户，随机初始密码在/var/log/mysqld.log文件中

        [root@localhost ~]# mysqld --initialize --user=mysql

 - 初始化生成无密码 root 账户

        [root@localhost ~]# mysqld --initialize-insecure --user=mysql

### 修改编码

    [root@localhost ~]# vim /etc/my.cnf

    [client]
    default-character-set = utf8
    [mysqld]
    character_set_server = utf8
    port = 3030
    lower_case_table_names = 1

### 启动mysql

    [root@localhost ~]# systemctl restart mysqld

### 修改密码

    mysql> alter user 'root'@'localhost' identified by '123456';

### 配置远程访问

    mysql> use mysql;
    mysql> update user set host='%' where user = 'root';
    mysql> flush privileges;

### 创建数据库并授权用户

    create database if not exists dbname default charset utf8 collate utf8_general_ci;

    grant all on dbname.* to 'julei'@'%' identified by '4YDf1r93';

### 创建用户

    create user 'julei'@'%' identified by '4YDf1r93';

### 备注

    mysql> alter user'root'@'localhost' identified with mysql_native_password

[在线安装](https://dev.mysql.com/doc/mysql-yum-repo-quick-guide/en/#repo-qg-yum-fresh-install)

## centos8（mysql8.0）

### 安装

    [root@localhost ~]# yum install @mysql:8.0 -y

### 启动MySQL8.0服务和开机启动

    [root@localhost ~]# systemctl start mysqld
    [root@localhost ~]# systemctl enable mysqld

### 安全初始化

    [root@localhost ~]# mysql_secure_installation

### 创建用户

    create user 'julei'@'%' identified by '4YDf1r93';

### 创建数据库并授权用户

    create database if not exists dbname;

    grant all privileges on dbname.* to 'julei'@'%' with grant option;

## windows

### 在mysql目录下新建data文件夹

### 初始化

 - 执行以下命令初始化生成了一个无密码的root账户

        mysqld --initialize-insecure

 - 执行以下命令初始化生成随机密码的root账户，随机密码在 x:\mysql\data\xxx.err文件中

        mysqld --initialize

### 服务安装

    进入 X:\mysql\bin目录下，执行命令：

    mysqld --install 安装服务
    mysqld --remove 移除服务

### 配置编码

    [client]
    default-character-set = utf8
    [mysqld]
    basedir = D:\mysql
    datadir = D:\mysql\data
    port = 3306
    character_set_server = utf8
