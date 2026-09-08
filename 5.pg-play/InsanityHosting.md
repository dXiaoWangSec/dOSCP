参考资料：
 
[https://pssec.medium.com/insanity-1-insanity-hosting-vulnhub-pgplay-writeup-7185a94bb129](https://pssec.medium.com/insanity-1-insanity-hosting-vulnhub-pgplay-writeup-7185a94bb129)
   

[https://medium.com/@vaibhavc418/offensive-security-insanity-hosting-walkthrough-f036b27fcca9](https://medium.com/@vaibhavc418/offensive-security-insanity-hosting-walkthrough-f036b27fcca9)
   

分析过程是最重要的  
[https://siunam321.github.io/ctf/pgplay/GlasgowSmile/](https://siunam321.github.io/ctf/pgplay/GlasgowSmile/)
      

lianjie  
[http://192.168.146.124/monitoring/login.php](http://192.168.146.124/monitoring/login.php)
 
otis:123456
      

diyige  
┌──(kali㉿kali)-[~/Desktop/pg02/InsanityHosting]  
└─$ ssh elliot@192.168.146.124  
The authenticity of host '192.168.146.124 (192.168.146.124)' can't be established.  
ED25519 key fingerprint is SHA256:eCrkU/pjlo8f7sNUU6/DASra4biW9OuKmWxQptyXBdw.  
This key is not known by any other names.  
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes  
Warning: Permanently added '192.168.146.124' (ED25519) to the list of known hosts.  
elliot@192.168.146.124's password:  
[elliot@insanityhosting ~]$ ls  
local.txt  
[elliot@insanityhosting ~]$ cat local.txt  
c0e2ab1c18e7b661a9f22a1dbcf75719  
[elliot@insanityhosting ~]$
      

root:S8Y389KJqWpJuSwFqFZHwfZ3GnegUa
 
第一个：  
[root@insanityhosting elliot]# ls  
local.txt  
[root@insanityhosting elliot]# cat local.txt  
c0e2ab1c18e7b661a9f22a1dbcf75719  
[root@insanityhosting elliot]#
    
[elliot@insanityhosting esmhp32w.default-default]$  
[elliot@insanityhosting esmhp32w.default-default]$  
[elliot@insanityhosting esmhp32w.default-default]$ su root  
Password:  
[root@insanityhosting esmhp32w.default-default]# cd  
[root@insanityhosting ~]# ls  
flag.txt proof.txt  
[root@insanityhosting ~]# cat flag.txt  
Your flag is in another file...  
[root@insanityhosting ~]# cat proof.txt  
17299587a68638f5315e7de8e02bc636  
[root@insanityhosting ~]#