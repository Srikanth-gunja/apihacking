# Lab setUP
### we use 
     1)crapi - crapi.apisec.ai
     2)vapi  - vapi.apisec.ai

## Setup
1)crapi(completely ridiculous api):
bash```
$mkdir ~/lab 
$cd ~/lab
#sudo curl -o docker-compose.yml https://raw.githubusercontent.com/OWASP/crAPI/main/deploy/docker/docker-compose.yml
$ sudo docker-compose pull
$ sudo docker-compose -f docker-compose.yml --compatibility up -d
```
Note: http://127.0.0.1:8888 (crAPI landing page) ,, http://127.0.0.1:8025  (crAPI Mailhog Server).
to stop use
bash```
$sudo docker-compose stop
```
2)vapi
bash```
$cd ~/lab
$sudo git clone https://github.com/roottusk/vapi.git
$cd /vapi
$sudo docker-compose up -d
```