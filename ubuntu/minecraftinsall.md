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
    > **소규모 서버** 추천
    
- [Tuinity(튜이니티)](https://github.com/Tuinity/Tuinity)
    API : Bukkit API, Spigot API, Paper API, Tuinity API
    지원 로더 : [버킷 플러그인](https://dev.bukkit.org/bukkit-plugins), [스피곳 플러그인](https://www.spigotmc.org/resources/categories/spigot.4/), [페이퍼 플러그인](https://papermc.io/forums/c/plugin-releases/15), 튜이니티 플러그인
    특징: 페이퍼 버킷을 최적화 해서 페이퍼 버킷보다 성능은 더 좋다. 페이퍼 버킷에서 작동되는 플러그인 중 호환성 문제는 없다.
    > **대규모 서버** 추천
    
- [Purpur(퍼퍼)](https://purpur.pl3x.net/downloads/#1.16.5)
    API : Bukkit API, Spigot API, Paper API, Tuinity API, Purpur API
    지원 로더 : [버킷 플러그인](https://dev.bukkit.org/bukkit-plugins), [스피곳 플러그인](https://www.spigotmc.org/resources/categories/spigot.4/), [페이퍼 플러그인](https://papermc.io/forums/c/plugin-releases/15), 튜이니티 플러그인, 퍼퍼 플러그인
    특징: 주로 마인크래프트의 시스템을 purpur.yml 로 수정할 수 있도록 커스터마이징에 초점을 맞춘 버킷이며, 이 역시 Tuinity 처럼 대규모 서버를 열 생각이라면 이 버킷을 추천한다.
    > **[서버를 최적화](https://github.com/YouHaveTrouble/minecraft-optimization)** 
    > **대규모 서버** 추천
    
> **플러그인 + 모드 서버**
- [Arclight(아크라이트)](https://github.com/IzzelAliz/Arclight)
    API : Forge Mod Loader, Bukkit, Spigot
    지원 로더 : [버킷 플러그인](https://dev.bukkit.org/bukkit-plugins), [스피곳 플러그인](https://www.spigotmc.org/resources/categories/spigot.4/), [포지 모드](https://www.curseforge.com/minecraft/mc-mods)
    특징: Magma, Mohist, CatServer 처럼 포지와 스피곳을 모두 호환하는 하이브리드 버킷이며, 최신버전 하이브리드 버킷중 가장 안정적이다.
    
> **모드서버**
- [Forge(포지)](https://files.minecraftforge.net/net/minecraftforge/forge/)
    API : ForgeModLoader API
    지원 로더 : [포지 모드](https://www.curseforge.com/minecraft/mc-mods)
    특징: 포지 모드 서버 구동에 사용되는 서버 프로그램. 플러그인은 호환되지 않지만 비슷한 역할을 하는 서버용 모드나 포지 모드로 포트된 플러그인을 대신 사용 가능하다.
    
- [Fabric(패브릭)](https://purpur.pl3x.net/downloads/#1.16.5)
    API : Fabric API
    지원 로더 : [패브릭 모드](https://www.curseforge.com/minecraft/mc-mods)
    특징: 
    




![image](https://user-images.githubusercontent.com/62547528/127183197-bde55920-f119-4cb8-b028-1ad3c8d16aa4.png)

중원하는 버킷 설치

> **나무위키** - 대규모 서버를 만들 때는 Tuinity를 추천하고, 최적화와 커스터마이징까지 원한다면 Purpur를 추천한다.


