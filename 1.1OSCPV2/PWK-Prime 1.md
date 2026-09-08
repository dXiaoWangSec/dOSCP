[https://infosecwriteups.com/vulnhub-prime-1-writeup-oscp-prep-by-dollarboysushil-ce36ce47768e](https://infosecwriteups.com/vulnhub-prime-1-writeup-oscp-prep-by-dollarboysushil-ce36ce47768e)
 
信息探测：  
sudo netdiscover  
Currently scanning: 172.16.158.0/16 | Screen View: Unique Hosts   15 Captured ARP Req/Rep packets, from 4 hosts. Total size: 900  
_____________________________________________________________________________  
IP At MAC Address Count Len MAC Vendor / Hostname  
-----------------------------------------------------------------------------  
192.168.163.147 00:0c:29:75:44:ba 7 420 VMware, Inc.  
192.168.163.1 00:50:56:fd:d3:ad 6 360 VMware, Inc.  
192.168.163.14 00:50:56:c0:00:08 1 60 VMware, Inc.  
192.168.163.254 00:50:56:fe:cf:75 1 60 VMware, Inc.
    
┌──(kali㉿kali)-[~]  
└─$ sudo nmap -sC -sV -p- 192.168.163.147  
Starting Nmap 7.94SVN ( [https://nmap.org](https://nmap.org) ) at 2025-07-05 06:37 EDT  
Nmap scan report for 192.168.163.147  
Host is up (0.0015s latency).  
Not shown: 65533 closed tcp ports (reset)  
PORT STATE SERVICE VERSION  
22/tcp open ssh OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 (Ubuntu Linux; protocol 2.0)  
| ssh-hostkey:  
| 2048 8d:c5:20:23:ab:10:ca:de:e2:fb:e5:cd:4d:2d:4d:72 (RSA)  
| 256 94:9c:f8:6f:5c:f1:4c:11:95:7f:0a:2c:34:76:50:0b (ECDSA)  
|_ 256 4b:f6:f1:25:b6:13:26:d4:fc:9e:b0:72:9f:f4:69:68 (ED25519)  
80/tcp open http Apache httpd 2.4.18 ((Ubuntu))  
|_http-server-header: Apache/2.4.18 (Ubuntu)  
|_http-title: HacknPentest  
MAC Address: 00:0C:29:75:44:BA (VMware)  
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
 
Service detection performed. Please report any incorrect results at [https://nmap.org/submit/](https://nmap.org/submit/) .  
Nmap done: 1 IP address (1 host up) scanned in 8.12 seconds   ┌──(kali㉿kali)-[~]  
└─$
   

┌──(kali㉿kali)-[~]  
└─$ [gobuster dir -u [http://192.168.163.147](http://192.168.163.147) -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt  ](https://github.com/Hidashimora/free-vpn-anti-rkn)
===============================================================  
Gobuster v3.6  
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)  
===============================================================  
[+] Url: [http://192.168.163.147](http://192.168.163.147)  
[+] Method: GET  
[+] Threads: 10  
[+] Wordlist: /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt  
[+] Negative Status codes: 404  
[+] User Agent: gobuster/3.6  
[+] Timeout: 10s  
===============================================================  
Starting gobuster in directory enumeration mode  
===============================================================  
/wordpress (Status: 301) [Size: 322] [--\> [http://192.168.163.147/wordpress/](http://192.168.163.147/wordpress/)]  
/dev (Status: 200) [Size: 131]  
/javascript (Status: 301) [Size: 323] [--\> [http://192.168.163.147/javascript/](http://192.168.163.147/javascript/)]  
/server-status (Status: 403) [Size: 303]  
Progress: 220560 / 220561 (100.00%)  
===============================================================  
Finished  
===============================================================   ┌──(kali㉿kali)-[~]  
└─$
 
┌──(kali㉿kali)-[~]  
└─$ gobuster dir -u [http://192.168.163.147/wordpress -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt](http://192.168.163.147/wordpress%20-w%20/usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt)  
===============================================================  
Gobuster v3.6  
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)  
===============================================================  
[+] Url: [http://192.168.163.147/wordpress](http://192.168.163.147/wordpress)  
[+] Method: GET  
[+] Threads: 10  
[+] Wordlist: /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt  
[+] Negative Status codes: 404  
[+] User Agent: gobuster/3.6  
[+] Timeout: 10s  
===============================================================  
Starting gobuster in directory enumeration mode  
===============================================================  
/wp-content (Status: 301) [Size: 333] [--\> [http://192.168.163.147/wordpress/wp-content/](http://192.168.163.147/wordpress/wp-content/)]  
/wp-includes (Status: 301) [Size: 334] [--\> [http://192.168.163.147/wordpress/wp-includes/](http://192.168.163.147/wordpress/wp-includes/)]  
/wp-admin (Status: 301) [Size: 331] [--\> [http://192.168.163.147/wordpress/wp-admin/](http://192.168.163.147/wordpress/wp-admin/)]  
Progress: 49903 / 220561 (22.63%)
 
Progress: 52934 / 220561 (24.00%)
 
Progress: 220560 / 220561 (100.00%)  
===============================================================  
Finished  
===============================================================   ┌──(kali㉿kali)-[~]  
└─$
    
三组链接  
[http://192.168.163.147/dev](http://192.168.163.147/dev)  
[http://192.168.163.147/worpress](http://192.168.163.147/worpress)  
[http://192.168.163.147/wordpress/wp-login.php?redirect_to=http%3A%2F%2F192.168.163.147%2Fwordpress%2Fwp-admin%2F&reauth=1](http://192.168.163.147/wordpress/wp-login.php?redirect_to=http%3A%2F%2F192.168.163.147%2Fwordpress%2Fwp-admin%2F&reauth=1)
    
web wordpress 密码  
victor：floow_the_ippsec
   

访问链接  
[http://192.168.163.147/wordpress/wp-admin/theme-editor.php?file=secret.php&thme=twentynineteen](http://192.168.163.147/wordpress/wp-admin/theme-editor.php?file=secret.php&thme=twentynineteen)  
web wordpress 密码  
victor：floow_the_ippsec
 
上传反向shell
   

web访问访问  
[http://192.168.163.147/wordpress/wp-content/themes/twentynineteen/secret.php](http://192.168.163.147/wordpress/wp-content/themes/twentynineteen/secret.php)

![[PWK-Prime 1 image 24f756039b31eef4.png|Exported image]]  

拿到shell

![[PWK-Prime 1 image 5bd045f59452bc71.png|Exported image]]   
都可以进行提权

![[PWK-Prime 1 image 0817647a29841190.png|Exported image]]   ![[PWK-Prime 1 image f6e23105a045442f.png|Exported image]]  

直接提权到root用户

![[PWK-Prime 1 image 91cd2a7f4d3551b8.png|Exported image]]   
第二种当时提权 提权可以升级成功下一步就是搞定远程内存提权
 ![[PWK-Prime 1 image 508c8ed5c4211d04.png|Exported image]]  
![[PWK-Prime 1 image b988fd661b6b864b.png|Exported image]]