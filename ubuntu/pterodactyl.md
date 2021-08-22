# [우분투](https://ubuntu.com/download/server)로 서버만들기!


**튜토리얼**

- [🌏](https://github.com/TWOJOB/server/blob/main/ubuntu/ubuntu.md) 서버 컴퓨터에 [우분투](https://ubuntu.com/download/server) 설치
- [🎮](https://github.com/TWOJOB/server/blob/main/ubuntu/aaPanel.md) 마크 페널[[aaPanel](https://www.aapanel.com/index.html)] 설치 및 설정
- [🌐](https://github.com/TWOJOB/server/blob/main/ubuntu/ISPConfig.md) 웹 페널[[ISPConfig](https://www.ispconfig.org/)] 설치 및 설정
- [☁](https://github.com/TWOJOB/server/blob/main/ubuntu/nextcloud.md) 클라우드[[nextcloud](https://nextcloud.com/)] 설치 및 설정
- [🚀](https://github.com/TWOJOB/server/blob/main/ubuntu/minecraftinsall.md) [마크](https://www.minecraft.net/ko-kr)서버 시작 하기
- [🚀](https://github.com/TWOJOB/server/blob/main/ubuntu/wordpress.md) [워드프레스](https://ko.wordpress.org/download/) 다운로드 및 설치
- [🚀](https://github.com/TWOJOB/server/blob/main/ubuntu/gnuboard.md) [그누보드](https://sir.kr/g5_pds) 다운로드 및 설치

> **NOTE 1** - 👋 이 튜토리얼은 잘 모르는 사람이 기억하기 쉽게 하려고 만든 것입니다. 정확하지 않을 수도 있습니다.
>
> **NOTE 2** - 안되거나 오류가 나면 처음부터 다시 설치를 하다 보면 고쳐지기도 한다.   `50번 정도 다시 설치하면서 느낀거...`

----


## [pterodactyl](https://pterodactyl.io/) 설치하기

### Step 1: [pterodactyl](https://pterodactyl.io/panel/1.0/getting_started.html#picking-a-server-os) 설치


``` Linux
sudo su -

```


``` Linux
apt -y install software-properties-common curl apt-transport-https ca-certificates gnupg
```


``` Linux
LC_ALL=C.UTF-8 add-apt-repository -y ppa:ondrej/php
```


``` Linux
add-apt-repository -y ppa:chris-lea/redis-server
```


``` Linux
curl -sS https://downloads.mariadb.com/MariaDB/mariadb_repo_setup | sudo bash
```


``` Linux
apt update
```


``` Linux
apt -y install php8.0 php8.0-{cli,gd,mysql,pdo,mbstring,tokenizer,bcmath,xml,fpm,curl,zip} mariadb-server nginx tar unzip git redis-server
```


## Composer 설치


``` Linux
curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/local/bin --filename=composer
```


## 파일다운 로드


``` Linux
mkdir -p /var/www/pterodactyl
```


``` Linux
cd /var/www/pterodactyl
```


``` Linux
curl -Lo panel.tar.gz https://github.com/pterodactyl/panel/releases/latest/download/panel.tar.gz
```


``` Linux
tar -xzvf panel.tar.gz
```


``` Linux
chmod -R 755 storage/* bootstrap/cache/
```


``` Linux
cp .env.example .env
```


## 데이터 베에스 설정


``` Linux
mysql -u root -p
```
비밀번호 입력


``` Linux
CREATE USER 'pterodactyl'@'127.0.0.1' IDENTIFIED BY '[사용할 mrsql 비밀번호 입력]';
```


``` Linux
CREATE DATABASE panel;
```


``` Linux
GRANT ALL PRIVILEGES ON panel.* TO 'pterodactyl'@'127.0.0.1' WITH GRANT OPTION;
```


``` Linux
CREATE USER 'pterodactyluser'@'127.0.0.1' IDENTIFIED BY '[아까 입력한 비밀번호]';
```


``` Linux
GRANT ALL PRIVILEGES ON *.* TO 'pterodactyluser'@'127.0.0.1' WITH GRANT OPTION;
```


``` Linux
exit
```


------


``` Linux
composer install --no-dev --optimize-autoloader
```
yes


``` Linux
php artisan key:generate --force
```


``` Linux
php artisan p:environment:setup
```


이메일: 
주소: http://
시간: Asia/Seoul
나머지 넘기고
yes입력


``` Linux
php artisan p:environment:database
```
4번 Enter후 데이터 베이스 비밀번호 입력


## Database Setup


``` Linux
php artisan migrate --seed --force
```


## Add The First User


``` Linux
php artisan p:user:make
```


yes
이메일
유저이름
성
이름
비밀번호




## Set Permissions


``` Linux
chown -R www-data:www-data /var/www/pterodactyl/*
```


``` Linux
* * * * * php /var/www/pterodactyl/artisan schedule:run >> /dev/null 2>&1
```


## Create Queue Worker


``` Linux
cd /etc/systemd/system
```


``` Linux
cat > pteroq.service
```


``` Linux
# Pterodactyl Queue Worker File
# ----------------------------------

[Unit]
Description=Pterodactyl Queue Worker
After=redis-server.service

[Service]
# On some systems the user and group might be different.
# Some systems use `apache` or `nginx` as the user and group.
User=www-data
Group=www-data
Restart=always
ExecStart=/usr/bin/php /var/www/pterodactyl/artisan queue:work --queue=high,standard,low --sleep=3 --tries=3
StartLimitInterval=180
StartLimitBurst=30
RestartSec=5s

[Install]
WantedBy=multi-user.target
```


입력후
Ctrl+D


``` Linux
sudo systemctl enable --now redis-server
```


``` Linux
sudo systemctl enable --now pteroq.service
```


# Nginx With SSL


``` Linux
cd /etc/nginx/sites-available/
```


``` Linux
cat > pterodactyl.conf
```


``` Linux
server {
    listen 80;
    server_name <domain>;

    root /var/www/pterodactyl/public;
    index index.html index.htm index.php;
    charset utf-8;

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

    location = /favicon.ico { access_log off; log_not_found off; }
    location = /robots.txt  { access_log off; log_not_found off; }

    access_log off;
    error_log  /var/log/nginx/pterodactyl.app-error.log error;

    # allow larger file uploads and longer script runtimes
    client_max_body_size 100m;
    client_body_timeout 120s;

    sendfile off;

    location ~ \.php$ {
        fastcgi_split_path_info ^(.+\.php)(/.+)$;
        fastcgi_pass unix:/run/php/php8.0-fpm.sock;
        fastcgi_index index.php;
        include fastcgi_params;
        fastcgi_param PHP_VALUE "upload_max_filesize = 100M \n post_max_size=100M";
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        fastcgi_param HTTP_PROXY "";
        fastcgi_intercept_errors off;
        fastcgi_buffer_size 16k;
        fastcgi_buffers 4 16k;
        fastcgi_connect_timeout 300;
        fastcgi_send_timeout 300;
        fastcgi_read_timeout 300;
    }

    location ~ /\.ht {
        deny all;
    }
}
```


<domain>을 IP또는 자신의 도메인으로 수정후 입력


``` Linux
sudo ln -s /etc/nginx/sites-available/pterodactyl.conf /etc/nginx/sites-enabled/pterodactyl.conf
```


``` Linux
systemctl restart nginx
```


``` Linux

```


``` Linux

```


``` Linux

```


``` Linux

```


``` Linux

```


``` Linux

```


``` Linux

```


``` Linux

```


``` Linux

```


``` Linux

```


``` Linux

```


``` Linux

```


``` Linux

```


``` Linux

```


``` Linux

```


``` Linux

```


``` Linux

```


``` Linux

```


``` Linux

```


``` Linux

```


``` Linux

```


``` Linux

```


``` Linux

```


``` Linux

```


``` Linux

```


