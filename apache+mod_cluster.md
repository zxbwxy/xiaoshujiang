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
### centos安装mod_cluster 和apache

**下载mod_cluster**

将[mod_cluster-1.3.1.Final-linux2-x64-ssl.tar.gz ](http://mod-cluster.jboss.org/mod_cluster/downloads/1-3-1-Final-bin),解压到根目录，自带httpd模块,执行/opt/jboss/httpd/sbin/installhome.sh，生成默认配置文件


**修改配置**


Listen 8000 改成 Listen 192.168.66.130:80
LoadModule rewrite_module /opt/jboss/httpd/lib/httpd/modules/mod_rewrite.so 
216 ServerName 192.168.66.130:80





**启动apache** 
>/opt/jboss/httpd/sbin/apachectl start


http://192.168.66.130:8366/mod_cluster_manager





[Apache主配置文件httpd.conf 详解](https://www.linuxidc.com/Linux/2015-02/113921.htm)

[centOS 7 Apache服务的安装与配置](http://blog.51cto.com/13525470/2070375)

[Linux中Apache(httpd)安装、配置、加为服务](https://blog.csdn.net/u010297957/article/details/50751656)
http://middlewaremagic.com/jboss/?p=1952

[JBoss 系列二：使用Apache httpd(mod_cluster)和JBoss构架高可用集群环境](https://blog.csdn.net/kylinsoong/article/details/12292707/)

[Jboss7集群配置说明](https://blog.csdn.net/xixixi9988/article/details/21651449)
[Apache的Rewrite详解](https://www.jianshu.com/p/103742cccaff)
