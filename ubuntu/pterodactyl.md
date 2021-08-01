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
curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/local/bin --filename=composer
```
복사 후 PuTTY(SSH)에 입력

``` Linux
mkdir -p /var/www/pterodactyl
cd /var/www/pterodactyl
```
복사 후 PuTTY(SSH)에 입력

``` Linux
cp .env.example .env
composer install --no-dev --optimize-autoloader

# Only run the command below if you are installing this Panel for
# the first time and do not have any Pterodactyl Panel data in the database.
php artisan key:generate --force
```
복사 후 PuTTY(SSH)에 입력

``` Linux

```
복사 후 PuTTY(SSH)에 입력

``` Linux

```
복사 후 PuTTY(SSH)에 입력

``` Linux

```
복사 후 PuTTY(SSH)에 입력

``` Linux

```
복사 후 PuTTY(SSH)에 입력

### Step 2: SSH연결하기

`PuTTY(putty.exe)`를 킨후

Host Name
- `서버IP` 입력

Port
- `22` 입력

Connenction type
- `SSH` 선택

`Open` 클릭

### Step 3: SSH로그인하기

서버에 설치할때입력한 `아이디` 입력

서버에 설치할때입력한 `비밀번호` 입력


----


## [자동설치하기](https://github.com/vilhelmprytz/pterodactyl-installer)

### Step 1: [aaPanel](https://www.aapanel.com/index.html) 설치

[aaPanel](https://www.aapanel.com/index.html)사이트 접속후

Installation:
- Ubuntu/Deepin: 
``` Linux
wget -O install.sh http://www.aapanel.com/script/install-ubuntu_6.0_en.sh && sudo bash install.sh aapanel
```
복사 후 PuTTY(SSH)에 입력

``` Linux
Y
```
복사 후 PuTTY(SSH)에 입력


### Step 2: [aaPanel](https://www.aapanel.com/index.html) 설정
















