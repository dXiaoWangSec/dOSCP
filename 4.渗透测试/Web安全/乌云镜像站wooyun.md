**M06-Ubuntu虚拟机搭建乌云镜像站wooyun**
 
**1、下载虚拟机文件**  
部署了乌云镜像网站wooyun的Ubuntu虚拟机，13G大小  
链接： [https://pan.baidu.com/s/167f40kjjSEbedNOQtjyZfg?pwd=8888](https://pan.baidu.com/s/167f40kjjSEbedNOQtjyZfg?pwd=8888)  
得到分卷压缩的四个文件：

![[乌云镜像站wooyun image aaf096ce34c918b7.png|Exported image]]

**2、在本地用winrar解压**  
**选中4个rar文件**，右键解压

![[乌云镜像站wooyun image 697406d2f8685112.png|Exported image]]

**3、打开.vmx文件**  
vmware 文件——打开，找到解压出来的虚拟机目录，打开 .vmx文件

![[乌云镜像站wooyun image 9b397337101f8a09.png|Exported image]]

**4、启动虚拟机**  
启动虚拟机以后，只有一个172的内网IP，因为制作镜像时是挂起状态。  
**需要再重启一次**，才能得到NAT模式下的局域网IP。

![[乌云镜像站wooyun image 95c219b1ab4d1f53.png|Exported image]]

重启以后需要登录：  
用户名 hancool  
密码 qwe123  
使用ip addr命令查看虚拟机的IP。  
例如：IP 192.168.142.167  
**5、拉取最新数据**  
（因为源站早就关闭了，所以推测这个爬取最新数据没什么作用，但是还是执行一下。可以跳过）  

```
cd/home/hancool/wooyun_public/scrapy/wooyun￼scrapy crawl wooyun -apage_max=0-alocal_store=true -aupdate=true￼
```
 Copy  

```
cd/home/hancool/wooyun_public/scrapy/wooyun_drops￼scrapy crawl wooyun -apage_max=0-alocal_store=true -aupdate=true￼
```
 Copy  
**6、编写启动脚本**  
为了方便启动应用（特别是无法用xshell远程连接、不能粘贴命令的时候），在用户home目录下编写一键启动的shell脚本：  

```
cdvimrun.sh￼
```
 Copy  
脚本内容（注意目录不要敲错）：  

```
#!/bin/bash# 
```

==运行==

```
EScd/home/hancool/elasticsearch-2.3.4/bin￼./elasticsearch -d# 
```

==启动应用==

```
cd/home/hancool/wooyun_public/flask￼./app.py￼
```
 Copy  
增加权限：  
chmod +x run.sh  
运行：  
./run.sh （以后只要开机运行这个命令就行了）  
**7、访问**  
在IP后面加上5000端口访问：  
[http://192.168.142.167:5000](http://192.168.142.167:5000/)  
不带任何条件点击搜索按钮，可以查看所有漏洞/知识库文章

![[乌云镜像站wooyun image 4a64b5e83140f7a3.png|Exported image]]

效果：

![[乌云镜像站wooyun image aa45367564360c1d.png|Exported image]]  
![[乌云镜像站wooyun image 2aab4369e19378f4.png|Exported image]]

乌云回忆录  
[https://zhuanlan.zhihu.com/p/445863413](https://zhuanlan.zhihu.com/p/445863413)