---
title: apache+mod_cluster
tags: 
grammar_cjkRuby: true
---


## 开发环境
Jdk 1.8
Centos7
WildFly

概述
1.安装mod_cluster 和apache


下载：wget -O mod_cluster-1.3.1.Final-linux2-x64-ssl.tar.gz  http://downloads.jboss.org/mod_cluster//1.3.1.Final/linux-x86_64/mod_cluster-1.3.1.Final-linux2-x64-ssl.tar.gz&& tar -xzvfmod_cluster-1.3.1.Final-linux2-x64-ssl.tar.gz -C /&& rm -rf mod_cluster-1.3.1.Final-linux2-x64-ssl.tar.gz
校验：

> /opt/jboss/httpd/sbin/apachectl start|stop|restart

http://192.168.66.130:8366/mod_cluster_manager





[Apache主配置文件httpd.conf 详解](https://www.linuxidc.com/Linux/2015-02/113921.htm)

[centOS 7 Apache服务的安装与配置](http://blog.51cto.com/13525470/2070375)

[Linux中Apache(httpd)安装、配置、加为服务](https://blog.csdn.net/u010297957/article/details/50751656)
http://middlewaremagic.com/jboss/?p=1952

[JBoss 系列二：使用Apache httpd(mod_cluster)和JBoss构架高可用集群环境](https://blog.csdn.net/kylinsoong/article/details/12292707/)

[Jboss7集群配置说明](https://blog.csdn.net/xixixi9988/article/details/21651449)
[Apache的Rewrite详解](https://www.jianshu.com/p/103742cccaff)
