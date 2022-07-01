# AzuraCast Installation
```
sudo apt update
```
```
sudo apt upgrade
```
```
sudo apt autoremove
```
```
adduser ahiska
```
```
usermod -aG sudo ahiska
```
```
su - ahiska
```
```
sudo ls -la /root
```
```
sudo timedatectl set-timezone "Europe/Istanbul"
```
```
sudo hostnamectl set-hostname server
```
```
sudo nano /etc/hosts
```
```
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```
```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
```
```
apt-cache policy docker-ce
```
```
sudo apt install docker-ce
```
```
sudo systemctl status docker
```
```
sudo usermod -aG docker ${USER}
```
```
groups
```
```
sudo usermod -aG docker ahiska
```
```
newgrp docker
```
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```
```
sudo chmod +x /usr/local/bin/docker-compose
```
```
docker-compose --version
```
```
sudo su -
```
```
mkdir -p /var/azuracast
```
```
cd /var/azuracast
```
```
curl -fsSL https://raw.githubusercontent.com/AzuraCast/AzuraCast/main/docker.sh > docker.sh
```
```
chmod a+x docker.sh
```
```
yes 'Y' | ./docker.sh setup-release
```
```
./docker.sh change-ports
```
```
yes '' | ./docker.sh install
```
```
su - ahiska
```
```
sudo apt install nginx
```
```
sudo systemctl start nginx
```
```
sudo systemctl enable nginx
```
```
sudo systemctl status nginx
```
```
sudo nano /etc/nginx/sites-available/default
```
```
server {
        listen 80;

        server_name ahiskaradyo.com www.ahiskaradyo.com;

        location / {
            proxy_pass http://localhost:8080;
        }
}
```
```
sudo service nginx configtest
```
```
sudo systemctl restart nginx
```
```
sudo systemctl status nginx
```
```
sudo ufw enable
```
```
sudo ufw allow 'Nginx Full'
```
```
sudo ufw allow 2022
```
```
sudo ufw allow 8063
```
