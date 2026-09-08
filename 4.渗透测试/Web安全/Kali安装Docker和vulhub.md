**Kali安装Docker和vulhub**
 
CentOS安装请参考：  
G12-CentOS安装vulhub靶场  
[https://wiki.bafangwy.com/doc/641/](https://wiki.bafangwy.com/doc/641/)  
本文演示在Kali安装docker并搭建vulhub靶场。  
**第一步：安装docker**  
1、更新软件  
apt-get update  
2、安装CA证书：  
apt-get install -y apt-transport-https ca-certificates

![[Kali安装Docker和vulhub image c120c588e3bd46a6.png|Exported image]]

3、安装docker：  
apt install docker.io  
4、查看docker是否安装成功：docker -v

![[Kali安装Docker和vulhub image e54c1e1622ad6b42.png|Exported image]]

5、启动docker：  
systemctl start docker  
6、显示docker信息：docker ps -a

![[Kali安装Docker和vulhub image eb07a6e3539cd680.png|Exported image]]

**第二步：安装docker-compose**  
**【方法1】**  
安装pip：  
apt-get install python3-pip ，可以通过pip --version版本查看  
安装docker-compose：  
pip install docker-compose  
这里是直接安装好了，不需要设置权限。  
如果报错，可以用下面的方法2。  
下面两种方法需要chmod设置权限↓↓↓  
**【方法2】**  
下载1.29.2 docker compose  
sudo curl -L "[https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)](https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$\(uname%20-s\)-$\(uname%20-m\))" -o /usr/local/bin/docker-compose  
如果github无法连接，可以用下面的方法3  
**【方法3】**  
如果以上两种方法都不行，可以直接从百度网盘下载docker-compose文件以后，传输到 /usr/local/bin目录（使用xshell）  
链接： [https://pan.baidu.com/s/1C9WQKVkmPbwc2g2n2TBCBg?pwd=8888](https://pan.baidu.com/s/1C9WQKVkmPbwc2g2n2TBCBg?pwd=8888)  
参考：  
[https://www.mashibing.com/question/detail/103797](https://www.mashibing.com/question/detail/103797)  
**给docker-compose设置权限**  
给文件增加可执行权限：  
chmod +x /usr/local/bin/docker-compose  
查看版本，是否安装成功：  
docker-compose -v

![[Kali安装Docker和vulhub image 038c5c31fb808871.png|Exported image]]

**第三步，将docker换成国内源**  
1、更改源：  
vim /etc/docker/daemon.json，修改为以下内容（原有内容全部删掉）：  
请看这篇文档，一直在更新，随时可能失效：  
[https://wiki.bafangwy.com/doc/693/](https://wiki.bafangwy.com/doc/693/)  
2、重启docker：  
systemctl restart docker  
3、查看信息：docker info，出现之前配置的信息即为成功

![[Kali安装Docker和vulhub image 6236f367d87e944b.png|Exported image]]

**第四步：下载vulhub**  
git clone [https://github.com/vulhub/vulhub.git](https://github.com/vulhub/vulhub.git)  
==如果无法从github下载靶场代码，也可以直接从网盘下载以后，使用xshell传输到虚拟机：==  
vulhub-20240527.zip  
[https://msb-netdisk.mashibing.com/share/c64a73ffcd0f4efe9afe9af3709f09fb](https://msb-netdisk.mashibing.com/share/c64a73ffcd0f4efe9afe9af3709f09fb)  
例如：  
cd /var/local  
mkdir soft  
cd soft  
把文件夹放在soft目录下后，解压：  
unzip vulhub-20240527.zip （改成你的压缩包名字）  
**第五步：使用vulhub靶场**  
1、进入vulhub的根目录  
例如：  
cd /var/local/soft/vulhub-master/  
ls  
如果不知道解压到哪里去了，就用这个命令搜索：  
find / -name "vulhub*"  
2、根目录下面是按组件名称命名的

![[Kali安装Docker和vulhub image 2806d7c2da2ec8e0.png|Exported image]]

想要复现哪个组件的漏洞，就进入哪个文件夹  
例如：  
cd weblogic  
ls  
3、  
组件名称下载是各种具体的漏洞，需要进一步进入具体的漏洞文件夹：

![[Kali安装Docker和vulhub image 9164bd78c035a62a.png|Exported image]]

例如：  
cd weak-password  
ls  
4、编辑某个靶场的配置文件（非必要操作）  
==注意：因为很多的靶场端口默认端口号是一样的，如果同时启动多个靶场可能会冲突。==  
如果要修改靶场端口号，使用以下命令：  
vim docker-compose.yml  
修改**左边的**这个端口号，这个是在物理机连接使用的端口号：

![[Kali安装Docker和vulhub image 6333de58313ac8bd.png|Exported image]]

**第六步：启动靶场**  
启动靶场环境（-d代表后台启动。如果需要查看日志，可以去掉-d）：  
docker-compose up -d  
==注意，由于网络等问题，拉取镜像失败，或者启动容器失败，都是正常的。==  
==解决办法：Ctrl+C中断，再次使用docker-compose up -d命令重新拉取即可。==  
**容器管理**  
以下命令都要在靶场目录里面操作（也就是有docker-compose.yml的目录）  
查看当前启动环境：  
docker-compose ps  
这样可以通过本机的ip:端口号（[http://192.168.198.140:8080/）](http://192.168.198.140:8080/%EF%BC%89) 进行靶场访问  
停止靶场：  
docker-compose stop  
若不需要使用该靶场的时候，可移除环境：  
docker-compose down  
移除后就不能访问该网址了  
**Docker常用命令**  
[https://wiki.bafangwy.com/doc/698/](https://wiki.bafangwy.com/doc/698/)  
**问题汇总**  
【汇总】docker-compose报错  
[https://wiki.bafangwy.com/doc/492/](https://wiki.bafangwy.com/doc/492/)  
【汇总】vulhub靶场无法启动/连接  
[https://wiki.bafangwy.com/doc/227/](https://wiki.bafangwy.com/doc/227/)