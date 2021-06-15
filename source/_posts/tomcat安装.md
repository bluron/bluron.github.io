---
title: tomcat安装
date: 2021-06-15 17:22:54
---

### 解压缩

    [root@localhost local]# tar -zxf apache-tomcat-7.0.85.tar.gz

### 重命名

    [root@localhost local]# mv apache-tomcat-7.0.85 tomcat
<!-- more -->
### 设置tomcat开机启动

    [root@localhost local]# vim /etc/rc.d/rc.local

    export JAVA_HOME=/usr/local/java/jdk1.8.0_191
    /usr/local/tomcat/bin/startup.sh start

### 修改rc.local权限

    [root@localhost local]# chmod 755 /etc/rc.d/rc.local
