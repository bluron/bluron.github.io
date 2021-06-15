---
title: weblogic安装
date: 2021-06-15 17:19:57
---

### 安装x11

    [root@localhost ~]# yum -y install xorg-x11-xauth xorg-x11-utils

### 安装jdk

    [root@localhost local]# vim /etc/profile

    export JAVA_HOME=/usr/local/java/jdk1.8.0_191
    export PATH=$PATH:$JAVA_HOME/bin

    [root@localhost local]# source /etc/profile
<!-- more -->
### 创建用户

    [root@localhost ~]# groupadd dba
    [root@localhost ~]# useradd -g dba weblogic
    [root@localhost ~]# passwd weblogic

### 创建安装目录

    [root@localhost ~]# mkdir -p /u02/
    [root@localhost ~]# chown -R weblogic:dba /u02/

### 安装

    [weblogic@localhost ~]$ java -jar fmw_12.2.1.3.0_wls.jar
