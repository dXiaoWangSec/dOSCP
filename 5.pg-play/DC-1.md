参考资料：  
[https://medium.com/@haadimdwork/dc-1-walkthrough-oscp-proving-grounds-4b35c06dc121](https://medium.com/@haadimdwork/dc-1-walkthrough-oscp-proving-grounds-4b35c06dc121)
   

192.168.212.193
 
droopescan scan drupal -u [http://192.168.212.193/](http://192.168.212.193/)
   

msfconsole
   

python -c 'import pty; pty.spawn("/bin/bash")'
      

diyige  
www-data@DC-1:/home$ cat local.txt  
cat local.txt  
c9e5bdceb26df41d21d08c1440275e63  
www-data@DC-1:/home$
    
tiquan  
 
proof.txt thefinalflag.txt  
bash-4.2# cat proof.txt  
cat proof.txt  
5116d68d60e9c00e5789b216b4ff26d3  
bash-4.2#
   

bash-4.2# uname -a  
uname -a  
Linux DC-1 3.2.0-6-486 #1 Debian 3.2.102-1 i686 GNU/Linux  
bash-4.2# cat /etc/*-release  
cat /etc/*-release  
PRETTY_NAME="Debian GNU/Linux 7 (wheezy)"  
NAME="Debian GNU/Linux"  
VERSION_ID="7"  
VERSION="7 (wheezy)"  
ID=debian  
ANSI_COLOR="1;31"  
HOME_URL="http://www.debian.org/"  
SUPPORT_URL="http://www.debian.org/support/"  
BUG_REPORT_URL="http://bugs.debian.org/"  
bash-4.2#