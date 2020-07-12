---
title: Linux Commandline
layout: default
parent: Others
nav_order: 3
---

# Linux CommandLine
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}


```shell
adduser _user123_  #user123 is the name of a new user
#it will ask a password for user123

-aG sudo user123 # assign sudo privilege to user123
sudo su - user123 # switch a Terminal user to user123  

sudo apt update #update apt 

sudo groupadd tomcat #create a new group 'tomcat'
curl -O http://miroors.../tomcat.tar.gz #URL of file download

cd /temp # if starts with '/', it's absolute path. (root)/temp
ls -al /
sudo mkdir /opt/tomcat #create 'tomcat' folder in (root)/opt folder
sudo tar xzvf apache-..tar.gz -C /opt/tomcat --strip-components=1  #install tomcat file (apache-..tar.gz) in /opt/tomcat folder 

chgrp --help #if wanna know how to use command line (eg- 'chrgp') , then check with --help
sudo chgrp -R tomcat /opt/tomcat # assign the group of 'tomcat' to sudo for all folders in /opt/tomcat 

ls /opt/tomcat
sudo chmod -R g+r conf
sudo chmod g+x conf
sudo chown -R tomcat wepapps/ work/ temp/ logs/

sudo update-java-alternatives -l #check 'JAVA_HOME' environmental variable in Linux

sudo ufw allow 8080 #open firewall to port 8080
ip addr show #check ip address - inet
sudo systemctl status tomcat #can check if tomcat is runnning or not

sudo /opt/tomcat/bin/startup.sh

tail -f /opt/tomcat/logs/catalina.-.log #log file name, it reads an active live log file 

sudo nano filename.txt  #text editor

sudo apt seaerch #search available apt packages
sudo apt install notepadqq #install program by using apt (eg- notepad++)


sudo ufw status # check firewall status with open ports
sudo ufw allow 22 # it opens port 22 on firewall
sudo ufw deny 22 # it closes port 22 on firewall 

ps -ef | grep java  # it grabs pid of executed java 
sudo kill -9 <pid>
```


mysql

```shell
sudo service mysql start #start mysql server
sudo service mysql restart #restart mysql server 

sudo mysql -u root -p #login mysql as root 
quit #exit mysql

# create user 'username123' at server1 and allow its access to server1. server2 can access to server1 by using 'username123'.
CREATE USER 'username123'@'localhost' IDENTIFIED BY 'some_password';
GRANT ALL PRIVILEGES ON *.* TO 'username123'@'localhost' WITH GRANT OPTION;
CREATE USER 'username123'@'%' IDENTIFIED BY 'some_password';
GRANT ALL PRIVILEGES ON *.* TO 'username123'@'%' WITH GRANT OPTION;
```


![](/assets/images/others001.jpg)
