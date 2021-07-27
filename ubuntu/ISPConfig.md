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


## [PuTTY](https://www.putty.org/) 설치하기

### Step 1: [PuTTY](https://www.putty.org/) 설치

`[PuTTY 다운로드](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)`사이트에 접속후

putty.exe (the SSH and Telnet client itself) 버전(64-bit x86) `putty.exe`

> **NOTE** - SSH버전 또는 통합버전 설치

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


## [ISPConfig](https://www.ispconfig.org/) 설치 및 설정하기

### Step 1: [ISPConfig](https://www.ispconfig.org/) 설치

apt-get업대이트
``` Linux
sudo apt-get update
```

apt-get업그레이드
``` Linux
sudo apt-get upgrade
```

서버 다시시작
``` Linux
sudo reboot
```

``` Linux
hostnamectl set-hostname server.example.com
```
`server.example.com`위치에 자신의 서버주소(server.도메인) 입력

``` Linux
sudo -s
```

``` Linux
cd /tmp
git clone https://git.ispconfig.org/ispconfig/ispconfig-autoinstaller.git
cd ispconfig-autoinstaller
./ispc3-ai.sh
```


``` Linux
yes
```
입력


### Step 2: [ISPConfig](https://www.ispconfig.org/) 설정
















