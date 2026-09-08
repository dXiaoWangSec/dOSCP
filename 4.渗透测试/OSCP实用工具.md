# useful tools
一些用户反映，在 OSCP Kali 版本上通过 apt 安装 pip3 会导致主机不稳定。在这种情况下，可以通过运行以下命令来安装 pip3：

`curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py python3 get-pip.py`

```
#oscp recon tool
git clone https://github.com/Tib3rius/AutoRecon.git /opt/AutoRecon
pip3 install -r /opt/AutoRecon/requirements.txt

#seclists
sudo apt install seclists

#nmap vulners
git clone https://github.com/vulnersCom/nmap-vulners /opt/nmap-vulners
cp /opt/nmap-vulners/vulners.nse /usr/share/nmap/scripts/
nmap --script-updatedb

# python unicorn for powershell meterpreter shells
git clone https://github.com/trustedsec/unicorn.git /opt/unicorn

# evil-winrm
sudo gem install winrm winrm-fs colorize stringio
git clone https://github.com/Hackplayers/evil-winrm.git
cd evil-winrm
# Usage: ruby evil-winrm.rb -i 192.168.1.100 -u Administrator -p 'MySuperSecr3tPass123!' -s '/home/foo/ps1_scripts/' -e '/home/foo/exe_files/'

# impacket
git clone https://github.com/SecureAuthCorp/impacket /opt/impacket
pip3 install /opt/impacket

# autorecon
RUN git clone https://github.com/Tib3rius/AutoRecon.git /opt/AutoRecon


# cms
RUN wpscan --update

# searchsploit
searchsploit -u



```