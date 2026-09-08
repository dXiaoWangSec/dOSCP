[https://www.vulnhub.com/entry/breach-301,177/](https://www.vulnhub.com/entry/breach-301,177/)
   

参考教程  
[https://medium.com/@rishikeshkhot26/vulnhub-fristileaks-1-3-challenge-walkthrough-391d4c076ef5](https://medium.com/@rishikeshkhot26/vulnhub-fristileaks-1-3-challenge-walkthrough-391d4c076ef5)
 
[https://lonelysec.com/vulnhub-x-fristileaks-1-3/](https://lonelysec.com/vulnhub-x-fristileaks-1-3/)
    
[http://192.168.163.129/fristi/do_upload.php](http://192.168.163.129/fristi/do_upload.php)
    
解码代码：
 
import base64  
in_string = "=RFn0AKnlMHMPIzpyuTI0ITG"  
in_string_1 = in_string[::-1]  
in_string_2 = in_string_1.encode("rot13")  
print (base64.b64decode(in_string_2))
    
内核进行提权  
#用于在Exploit Database（Exploit数据库）中搜索漏洞利用代码的命令行工具。你可以使用它来查找特定软#件或系统版本的漏洞利用代码。在你的请求中，你想要搜索Linux Kernel版本2.6.32的漏洞利用代码。
 
searchsploit Linux Kernel 2.6.32  
[https://www.exploit-db.com/exploits/40839](https://www.exploit-db.com/exploits/40839)