[https://www.vulnhub.com/entry/wintermute-1,239/](https://www.vulnhub.com/entry/wintermute-1,239/)  
参考资料：  
[https://seekorswim.github.io/walkthroughs/2019/05/01/wintermute-1/](https://seekorswim.github.io/walkthroughs/2019/05/01/wintermute-1/)
      

python创新虚拟环境：  
Python2/Python3使用virtualenv创建虚拟环境venv  
Python2使用virtualenv创建虚拟环境  
1. 安装virtualenv ：  
pip2 install virtualenv  
2. 在当前目录创建虚拟环境命令：  
python2 -m virtualenv ven2  
3. 进入虚拟环境：  
source venv2/bin/activate  
4. python --version  
Python 2.7.18  
5. 退出虚拟环境：deactivate
    

Python3使用virtualenv创建虚拟环境  
1. 安装virtualenv ：  
pip3 install virtualenv  
2. 在当前目录创建虚拟环境命令：  
python3 -m virtualenv venv3  
3. 进入虚拟环境：source venv3/bin/activate  
4. python --version  
Python 3.7.6  
5. 退出虚拟环境：deactivate  
更改为国内源：  
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple  
pip install --upgrade pip
   

python2命令
 
python -m SimpleHTTPServer port_number
 
python3命令  
python -m http.server port_number  
启动后在其他可ping通的服务器上使用命令
 
wget ip:port_number/file_name  
————————————————