Links: [[PROGRAMMING]]
Rel: [[git]]
Ref: https://docs.gitea.io/en-us

192.168.1.13
database - Thisdatarata!
curtis - assassassdollarsign!
alice - 
git - weinersandbutts


--- 
https://www.youtube.com/watch?v=y9zDbMkuXdE

http://192.168.1.13:3000

```
sudo apt-get update && sudo apt-get upgrade
sudo apt autoremove -y
sudo apt-get install git mariadb-server

sudo mysql_secure_installation

mysql

CREATE DATABASE gitea;
GRANT ALL PRIVILEGES ON gitea.* TO 'gitea'@'localhost' IDENTIFIED BY 'ENTERPASSWORD';
FLUSH PRIVILEGES;

exit

sudo adduser --disabled-login --gecos 'Gitea' git

sudo mkdir /home/git/gitea/
cd /home/git/gitea/
wget -O gitea https://dl.gitea.io/gitea/1.14.2/gitea-1.14.2-linux-arm-6

sudo mkdir custom/
sudo mkdir custom/conf/
sudo touch custom/conf/app.ini
sudo chmod 777 custom/conf/app.ini
# ^^ leave empty on init will fill

sudo ./gitea web
# -> localip:3000/install
# -> ... set up user -> 
sudo systemctl enable ssh
sudo systemctl start ssh
sudo passwd git # why not secure?
```
... needed? 
/etc/systemd/system/gitea.service
```sh
sudo touch /etc/systemd/system/gitea.service
sudo nano /etc/systemd/system/gitea.service
```
https://github.com/go-gitea/gitea/blob/main/contrib/systemd/gitea.service
-> edits
```sh
Wants=mariadb.service
After=mariadb.service

[Unit]
Description=Gitea (Git with a cup of tea)
After=syslog.target
After=network.target

[Service]
# Modify these two values and uncomment them if you have
# repos with lots of files and get an HTTP error 500 because
# of that
###
#LimitMEMLOCK=infinity
#LimitNOFILE=65535
RestartSec=2s
Type=simple
User=git
Group=git
WorkingDirectory=/user/git/gitea/
ExecStart=/home/git/gitea/gitea web
Restart=always
Environment=USER=git HOME=/home/git GITEA_WORK_DIR=/home/git/gitea

[Install]
WantedBy=multi-user.target

```

locally (commit)):
```sh
mkdir test-gitea
cd test-gitea
git init
touch README.md
echo "# Test 1 \n## Test 2\n### Test 3" >> README.md
git add README.md
git commit -m "init commit"
git remote add origin http://192.168.1.13:3000/curtis/test-gitea.git
git push -u origin master
# -> enter user credentials 
```

--- 

blah:
```
chown -R git:git /var/lib/gitea/
chmod -R 750 /var/lib/gitea/
mkdir /etc/gitea
chown root:git /etc/gitea
chmod 770 /etc/gitea # temporarily 
```

https://pimylifeup.com/raspberry-pi-gitea/
```sh
sudo apt-get update && sudo apt-get upgrade
sudo apt autoremove -y

sudo apt-get install  git mysql-server -y

sudo adduser --disabled-login --gecos 'Gitea' git

sudo mysql_secure_installation

mysql -u root -p

CREATE DATABASE gitea;
GRANT ALL PRIVILEGES ON gitea.* TO 'gitea'@'localhost' IDENTIFIED BY 'ENTERPASSWORD';
FLUSH PRIVILEGES;

exit

sudo su git

cd ~

mkdir gitea

cd gitea
wget https://dl.gitea.io/gitea/1.4.0/gitea-1.4.0-linux-arm-7 -O gitea
chmod +x gitea

sudo nano /etc/systemd/system/gitea.service
```

```sh
[Unit]
Description=Gitea (Git with a cup of tea)
After=syslog.target
After=network.target

[Service]
# Modify these two values ​​and uncomment them if you have
# repos with lots of files and get to HTTP error 500 because of that
###
# LimitMEMLOCK=infinity
# LimitNOFILE=65535
RestartSec=2s
Type=simple
User=git
Group=git
WorkingDirectory=/home/git/gitea
ExecStart=/home/git/gitea/gitea web
Restart=always
Environment=USER=git 
HOME=/home/git

[Install]
WantedBy=multi-user.target
```

```sh
sudo systemctl enable gitea.service
sudo systemctl start gitea.service
```

-> http://localipaddr:3000
^^ didn't work... called start via ./gitea web did