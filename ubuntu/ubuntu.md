# [우분투](https://ubuntu.com/download/server)로 서버만들기!


**튜토리얼**

- [🌏](https://github.com/TWOJOB/server/blob/main/ubuntu/ubuntu.md) 서버 컴퓨터에 [우분투](https://ubuntu.com/download/server) 설치
- [🎮](https://github.com/TWOJOB/server/blob/main/ubuntu/aaPanel.md) 마크 페널[[aaPanel](https://www.aapanel.com/index.html)] 설치 및 설정
- [🌐](https://github.com/TWOJOB/server/blob/main/ubuntu/ISPConfig.md) 웹 페널[[ISPConfig](https://www.ispconfig.org/)] 설치 및 설정
- [☁]() 클라우드[[nextcloud](https://nextcloud.com/)] 설치 및 설정
- [🚀]() [마크](https://www.minecraft.net/ko-kr)서버 시작 하기
- [🚀]() 커뮤니티 설치
- [🚀]() [워드프레스](https://ko.wordpress.org/download/) 다운로드 및 설치
- [🚀]() [그누보드](https://sir.kr/g5_pds) 다운로드 및 설치
- [🚀]() [Vditor](https://b3log.org/vditor/)

> **NOTE 1** - 👋 이 튜토리얼은 잘 모르는 사람이 기억하기 쉽게 하려고 만든 것입니다. 정확하지 않을 수도 있습니다.
>
> **NOTE 2** - 안되거나 오류가 나면 처음부터 다시 설치를 하다 보면 고쳐지기도 한다`그래서 50번 정도 다시 설치하면 서 알게 된 거...`

----


## 부팅 USB 만들기

### Step 1: [우분투](https://ubuntu.com/download/server) 설치

`[우분투](https://ubuntu.com/download/server)`사이트에 접속후

`Option 2` 클릭

`Download Ubuntu Server (최신버전) LTS` 클릭

> **NOTE** - 최신버전 또는 자신이 원하는 버전 설치

### Step 2: 부팅 가능한 USB 드라이브

[rufus](https://rufus.ie/ko/) 최신버전 설치

rufus실행후 USB선택

부트 선택옆 `선택` 버튼 클릭후 다운받은 .iso 파일 선택

`시작` 클릭

다운로드가 필요합니다.
- `예` 클릭

ISO 이미지 모드로 쓰기
- `OK` 클릭

USB 모든 데이터 삭제
- `확인` 클릭

## Install

### Step 1: 서버 컴퓨터 시작

서버 컴퓨터에 USB연결후 전원키키

부팅화면이 나오면 `F11(또는 F12)`을 눌러 바이오스 화면으로 이동후 USB(부팅USB)로 부팅

### Step 2: [우분투](https://ubuntu.com/download/server) 설치하기

language(언어 설정)
- `english` 선택(Enter)

Keyboard
- Layout: `english` 또는 `Korean`
- Variant: `english` 또는 `Korean`
- `Done` 클릭(Enter)

> **NOTE** - 영어로 선택해도 아직까지는 문제 없음

Network connections(고정IP 설정가능)
- `Done` 클릭(Enter)

Configure proxy(프록시 서버)
- `Done` 클릭(Enter)

Configure Ubuntu archive mirror(미러서버)
- `Done` 클릭(Enter)

Guided storage configurstion
- `Done` 클릭(Enter)

Storage configuraton
- `Done` 클릭(Enter)
- `Continue` 클릭(Enter)

Progile setup(계정생성)
- `이름입력` 예) TWOJOB
- `서버 이름입력` 예) ubuntu20
- `사용할 이름` 예) TWOJOB
- `비밀번호` 예) 1234
- `비밀번호 재입력` 예) 1234
- `Done` 클릭(Enter)

SSH Setup
- `Install OpenSSH server` 선택
- `Done` 클릭(Enter)

Featured server Snaps
- `Done` 클릭(Enter)


Installing system
- `Reeboot` 클릭(Enter)



