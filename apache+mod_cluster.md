---
title: apache+mod_cluster
tags: 
grammar_cjkRuby: true
---


## 开发环境
Jdk 1.8
Jboss http://jbossas.jboss.org/downloads/


1.安装mod_cluster 和apache
下载：wget -O mod_cluster-1.3.1.Final-linux2-x64-ssl.tar.gz  http://downloads.jboss.org/mod_cluster//1.3.1.Final/linux-x86_64/mod_cluster-1.3.1.Final-linux2-x64-ssl.tar.gz&& tar -xzvfmod_cluster-1.3.1.Final-linux2-x64-ssl.tar.gz -C /&& rm -rf mod_cluster-1.3.1.Final-linux2-x64-ssl.tar.gz
校验：
启动/opt/jboss/httpd/sbin/apachectl start


启动和关闭Apache服务

[root@localhost ~]# systemctl start httpd.service

[root@localhost ~]# systemctl stop httpd.service

cp /opt/jboss/httpd/sbin/apachectl /etc/rc.d/init.d/httpd 


[Apache主配置文件httpd.conf 详解](https://www.linuxidc.com/Linux/2015-02/113921.htm)

[centOS 7 Apache服务的安装与配置](http://blog.51cto.com/13525470/2070375)

[Linux中Apache(httpd)安装、配置、加为服务](https://blog.csdn.net/u010297957/article/details/50751656)
