
## Tools
1)Burp suite(with foxyproxy extension)
2)postman
3)mitmproxy2swagger
4)git,docker,go
5)jwt
6)kiterunner
7)Arjun
8)OWASP ZAP
## Tools install && setup
1)Burp suite
1.1:-install burp from google
1.2:-open burp->open new project->proxy->proxy settings->add 127.0.0.1:8080(to proxylisteners)
1.3:-install foxyporxy addon on firefox->click foxyproxy->options->proxies->add->Title:burp,Hostname:127.0.0.1,Port:8080(burp proxy)->save 
1.4:-select foxyproxy(burp) on browser->visit 
http://burpsuite ->click the CA certificates(dowanload certificate with .der extension)->settings->search certificates->view certificates->authorities->import->select downloaded der file.
2)Mitm(man in the middle)
bash```
$mitmweb ```
2.1:-go to http://mitm.it -> select firefox (mitm*.pem file)->settings->search certificates->view certificates->Authorities->import->select that downloaded file ->ok
Note:if you don`t add these cerificates it will give proxy error

3)Postman
bash```
$ sudo wget https://dl.pstmn.io/download/latest/linux64 -O postman-linux-x64.tar.gz && sudo tar -xvzf postman-linux-x64.tar.gz -C /opt && sudo ln -s /opt/Postman/Postman /usr/bin/postman
```
4)mitmproxy2swagger
bash```
$ sudo pip3 install mitmproxy2swagger
```
Note:if any errors occured ``` pip3 uninstall mitmproxy2swagger```reinstall it
5)
bash```
$ sudo apt-get install git
$ sudo apt-get install docker.io docker-compose
$ sudo apt install golang-go```
6)sublime
bash```
Install the GPG key:
$ wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/sublimehq-archive.gpg > /dev/null
Select the Stable channel:
$echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list
Update apt sources and install Sublime Text:
$sudo apt-get update
$sudo apt-get install sublime-text
```
7)kiterunner
bash```
$ sudo git clone  https://github.com/assetnote/kiterunner.git
$ cd kiterunner
$ sudo make build
$ sudo ln -s /opt/kiterunner/dist/kr /usr/bin/kr
```
8)Arjun
bash```
$ sudo git clone https://github.com/s0md3v/Arjun.git
```
9)OWASP ZAP
bash```
$ sudo apt install zaproxy
```
Note:Once ZAP is installed, make sure to navigate to the Manage Add-Ons (CTRL+U). Make sure to apply updates for the Fuzzer and OpenAPI Support.
10)Wordlists
bash```
SecLists (https://github.com/danielmiessler/SecLists)
$ sudo wget -c https://github.com/danielmiessler/SecLists/archive/master.zip -O SecList.zip \
&& sudo unzip SecList.zip \
&& sudo rm -f SecList.zip
Hacking-APIs (https://github.com/hAPI-hacker/Hacking-APIs)
$ sudo wget -c https://github.com/hAPI-hacker/Hacking-APIs/archive/refs/heads/main.zip -O HackingAPIs.zip \
&& sudo unzip HackingAPIs.zip \
&& sudo rm -f HackingAPIs.zip
```
11)json web token toolkit v2
bash```
$ cd /opt
$ sudo git clone https://github.com/ticarpi/jwt_tool
$ cd jwt_tool
$ python3 -m pip install termcolor cprint pycryptodomex requests
$ sudo chmod +x jwt_tool.py
$ sudo ln -s /opt/jwt_tool/jwt_tool.py /usr/bin/jwt_tool
```
