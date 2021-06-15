---
title: rabbitmq安装
date: 2021-06-15 17:23:39
---

### 安装erlang

    [root@julei ~]# vim /etc/yum.repos.d/rabbitmq-erlang.repo

    # In /etc/yum.repos.d/rabbitmq-erlang.repo
    [rabbitmq-erlang]
    name=rabbitmq-erlang
    baseurl=https://dl.bintray.com/rabbitmq-erlang/rpm/erlang/21/el/7
    gpgcheck=1
    gpgkey=https://dl.bintray.com/rabbitmq/Keys/rabbitmq-release-signing-key.asc
    repo_gpgcheck=0
    enabled=1

    [root@julei ~]# yum install erlang
<!-- more -->
### 安装rabbitmq

    [root@julei ~]# vim /etc/yum.repos.d/rabbitmq.repo

    [bintray-rabbitmq-server]
    name=bintray-rabbitmq-rpm
    baseurl=https://dl.bintray.com/rabbitmq/rpm/rabbitmq-server/v3.7.x/el/7/
    gpgcheck=0
    repo_gpgcheck=0
    enabled=1

    [root@julei ~]# yum install rabbitmq-server

### 启用web插件

    [root@julei ~]# rabbitmq-plugins enable rabbitmq_management

### 启动rabbitmq

    [root@julei ~]# systemctl start rabbitmq-server

### 创建用户

    [root@julei ~]# rabbitmqctl add_user julei 4YDf1r93
    [root@julei ~]# rabbitmqctl set_user_tags julei administrator
    [root@julei ~]# rabbitmqctl set_permissions -p / julei ".*" ".*" ".*"
