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
> **NOTE 2** - 안되거나 오류가 나면 처음부터 다시 설치를 하다 보면 고쳐지기도 한다   `50번 정도 다시 설치하면서 느낀거...`

----


## 서버에 자바 설치

### Step 1: java 설치

``` Linux
java -version
```
입력해 자바가 설치되어 있는지 확인

> **NOTE** - 자바가 설치되어있으면 오류가 날수있으니까 삭제후 설치

``` Linux
sudo add-apt-repository ppa:linuxuprising/java
```

``` Linux
sudo apt install oracle-java16-installer
```

> **NOTE** - 최신버전 또는 자신이 원하는 버전 설치

`확인` 클릭

`yes` 입력

### Step 1: java 확인

``` Linux
java -version
```
입력해 자바가 설치되었는지 확인

## 서버에 버킷 설치

- [바닐라 서버 기본](https://www.minecraft.net/download/server)(모장 공식 개발버전)
    특징: 버전 업데이트와 서버 업데이트가 같이 진행됨
    
- [CraftBukkit(크래프트버킷)](https://getbukkit.org/download/craftbukkit)
    API : Bukkit API
    지원 로더 : [버킷 플러그인](https://dev.bukkit.org/bukkit-plugins)
    
- [Spigot(스피곳)](https://getbukkit.org/download/spigot)
    API : Bukkit API, Spigot API
    지원 로더 : [버킷 플러그인](https://dev.bukkit.org/bukkit-plugins), [스피곳 플러그인](https://www.spigotmc.org/resources/categories/spigot.4/)
    
- [Paper(스피곳)](https://papermc.io/downloads)
    API : Bukkit API, Spigot API, Paper API
    지원 로더 : [버킷 플러그인](https://dev.bukkit.org/bukkit-plugins), [스피곳 플러그인](https://www.spigotmc.org/resources/categories/spigot.4/), [페이퍼 플러그인](https://papermc.io/forums/c/plugin-releases/15)
    특징: 비동기 청크 로딩등 다양한 최적화 패치 적용
    > **소규모 서버** 추천한다.
    
- [()]()
    Paper 포크
    특징: 업데이트가 가장빠름
    
- [()]()
    Paper 포크
    특징: 업데이트가 가장빠름
    
- [()]()
    Paper 포크
    특징: 업데이트가 가장빠름
    
- [()]()
    Paper 포크
    특징: 업데이트가 가장빠름
    
- [()]()
    Paper 포크
    특징: 업데이트가 가장빠름
    
- []()
    Paper 포크
    특징: 업데이트가 가장빠름
    




![image](https://user-images.githubusercontent.com/62547528/127183197-bde55920-f119-4cb8-b028-1ad3c8d16aa4.png)

중원하는 버킷 설치

> **나무위키** - 대규모 서버를 만들 때는 Tuinity를 추천하고, 최적화와 커스터마이징까지 원한다면 Purpur를 추천한다.


