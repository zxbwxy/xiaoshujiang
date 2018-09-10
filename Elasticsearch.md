---
title: 2018-9-10未命名文件 
tags: Elasticsearch
grammar_cjkRuby: true
---

一.环境搭建

1. win10下搭建linux环境
   下载 Vmware Workstation Pro
   	https://www.vmware.com/cn/products/workstation-pro/workstation-pro-evaluation.html
   下载centos iso镜像
   	https://www.centos.org/download/
   	http://mirrors.aliyun.com/centos/7/isos/x86_64/
   Vmware虚拟机设置静态IP地址
   	https://www.cnblogs.com/jsonhc/p/7685393.html
   	https://www.cnblogs.com/zhanjindong/p/3250393.html
2. linux下搭建学习环境
   2.1 安装JDK环境
   2.1 docker安装
   	Docker CE 镜像源站 https://yq.aliyun.com/articles/110806
   	镜像加速器https://dev.aliyun.com/search.html
   2.1 elk安装
   	安装elasticsearch
   	检测是否安装了Elasticsearch
       ps aux|grep elasticsearch1
   	安装JDK
   		安装JDK具体操作，请点击链接
   	安装Elasticsearch
       ## 下载&&解压
       wget --no-check-certificate --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-6.4.0.tar.gz&&tar -zxvf elasticsearch-6.4.0.tar.gz&&mv elasticsearch-6.4.0 /usr/local/elasticsearch
       ## 修改elasticsearch.yml
       cd /usr/local/elasticsearch
       vi elasticsearch.yml
       	##放开注释，并修改为本linux服务器 ip
       	network.host: 192.168.188.100 
       	discovery.zen.ping.unicast.hosts: ["192.168.188.100"]
       	
       vi /etc/sysctl.conf
       	#问题：max virutal memory areas vm.max_map_count [65530] is too low, increase to at least [262144]
       	#  解决方案：切换到root用户修改配置sysctl.conf  增加配置值： vm.max_map_count=655360
       	#执行命令 sysctl -p   这样就可以了，然后重新启动ES服务 就可以了
       	vm.max_map_count=262144
       	
       vi /etc/security/limits.conf 
       	#问题：max number of threads [3750] for user [xxx] is too low, increase to at least [4096]
       	#解决方案： 切到root 用户：进入到security目录下的limits.conf；执行命令 vim /etc/security/limits.conf 在文件的末尾添加下面的参数值
       	  * soft nofile 65536
       	  * hard nofile 131072
       	  * soft nproc 4096
       	  * hard nproc 4096
   
3. 插件安装
   
   
   参考：
   《死磕 Elasticsearch 方法论》https://blog.csdn.net/laoyang360/article/details/79293493
   Linux下安装Elasticsearch https://blog.csdn.net/y472360651/article/details/78670240?locationnum=8&fps=1


