参考资料：  
[https://github.com/pika5164/Offsec_Proving_Grounds/blob/master/PG_Practice/Linux/Wheels.md](https://github.com/pika5164/Offsec_Proving_Grounds/blob/master/PG_Practice/Linux/Wheels.md)
   

考察我们抓包注入 使用bp工具进行抓包
 
本实验将使用 XPATH 注入获取初始立足点，然后对二进制文件进行逆向工程，读取 /etc/shadow 文件的内容并破解 root 哈希值以获取 root 权限。本实验重点在于利用注入漏洞和提权方法。
      

本实验演示如何利用 Web 应用程序中的 XPath 注入漏洞来获取敏感信息，例如用户凭据。学员将使用这些凭据通过 SSH 获取初始访问权限。权限提升是通过逆向工程 SUID 二进制文件、利用路径遍历漏洞读取 /etc/shadow 文件的内容以及使用 hashcat 破解 root 密码哈希值来实现的。本实验重点讲解了 XPath 注入、逆向工程以及通过文件滥用实现权限提升等技术。
 
XPath  
XPath 注入攻击通过操控查询语句的结构，允许攻击者篡改查询逻辑，进而访问敏感数据或绕过认证。为了防范 XPath 注入，开发者应该采取严格的输入验证和过滤，使用参数化查询，并尽量避免手动构造 XPath 查
 
rustscan -a 192.168.161.202 -u 5000 -t 8000 --scripts -- -n -Pn -sVC
   

ffuf -u [http://192.168.161.202/FUZZ.php](http://192.168.161.202/FUZZ.php) -w /home/kali/SecLists/Discovery/Web-Content/directory-list-2.3-small.txt
   

root:$6$Hk74of.if9klVVcS$EwLAljc7.DOnqZqVOTC0dTa0bRd2ZzyapjBnEN8tgDGrR9ceWViHVtu6gSR.L/WTG398zZCqQiX7DP/1db3MF0:19123:0:99999:7:::
      

bob:$6$9hcN2TDv4v9edSth$KYm56Aj6E3OsJDiVUOU8pd6hOek0VqAtr25W1TT6xtmGTPkrEni24SvBJePilR6y23v6PSLya356Aro.pHZxs.:19123:0:99999:7:::  
mysql:!:19123:0:99999:7:::
         

john mima pojie  
ad7fff8819b9578c1ce2270910ceaeab
   

2 rows in set (0.000 sec)
 
MariaDB [wheels]\> select * from users;  
+----+----------+--------------------------------------------------------------+-----------------------+---------+  
| id | username | password | email | account |  
+----+----------+--------------------------------------------------------------+-----------------------+---------+  
| 1 | bob | $2a$12$XyDbORzX3TFxsdX2OJZLo.01jNZMrpi1iU3XqpW4IeqLbbUUBAGAm | bob@wheels.service | admin |  
| 2 | gurana | $2y$10$Im2ZQH9neNAUuM1LeUcNO.Hu.9p1qP2lQw59OtZKB.tmPrpRXoKmi | gurana@wheels.service | admin |  
| 3 | test | $2y$10$22bs4/jr.d9Sp8Y7O4K7FOBl2WdFev.j2f8tKcK95sGjda5GYLMIy | info@wheels.service | admin |  
+----+----------+--------------------------------------------------------------+-----------------------+---------+  
3 rows in set (0.000 sec)
 
MariaDB [wheels]\>
      

考察我们使用hash进行破解