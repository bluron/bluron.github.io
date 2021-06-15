---
title: nexus安装
date: 2021-06-15 17:24:10
---

### 修改nexus内存

    [root@localhost ~]# vim nexus-3.15.2-01/bin/nexus.vmoptions

### 修改nexus端口

    [root@localhost ~]# vim nexus-3.15.2-01/etc/nexus-default.properties

### 启动nexus

    [root@localhost ~]# ./nexus start
