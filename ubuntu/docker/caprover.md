## [caprover](https://caprover.com/)

### Step 0: docker 설치

### Step 1: caprover 설치


CapRover 설치
```
docker run -p 80:80 -p 443:443 -p 3000:3000 -v /var/run/docker.sock:/var/run/docker.sock -v /captain:/captain caprover/caprover
```


CapRover CLI 설치
```
npm install -g caprover
```


이미지 목록 보기
```
caprover serversetup
```


이미지 삭제
```
docker rmi 
```


실행중인 컨테이너 목록 보기
```
docker ps
```


모든 컨테이너 목록 보기
```
docker ps -a
```


컨테이너 만들기
```
docker run [options] image
```


옵션	설명
-d	      detached mode 흔히 말하는 백그라운드 모드
-p	      호스트와 컨테이너의 포트를 연결 (포워딩)
-v	       호스트와 컨테이너의 디렉토리를 연결 (마운트)
-e	      컨테이너 내에서 사용할 환경변수 설정
--name	  컨테이너 이름 설정
--it	    -i와 -t를 동시에 사용한 것으로 터미널 입력을 위한 옵션 (컨테이너의 표준 입력과 로컬 컴퓨터의 키보드 입력을 연결)
--rm	    프로세스 종료시 컨테이너 자동 제거
--link	  컨테이너 연결 [컨테이너 명:별칭]


컨테이너 시작
```
docker start 
```


컨테이너 재시작
```
docker restart 
```


컨테이너 접속
```
docker attach 
```


컨테이너 정지
```
docker stop 
```


컨테이너 삭제
```
docker rm 
```


이미지 목록 보기
```
docker pull 
```


이미지 목록 보기
```
docker pull 
```


이미지 목록 보기
```
docker pull 
```


이미지 목록 보기
```
docker pull 
```


이미지 목록 보기
```
docker pull 
```


이미지 목록 보기
```
docker pull 
```


이미지 목록 보기
```
docker pull 
```


이미지 목록 보기
```
docker pull 
```


이미지 목록 보기
```
docker pull 
```


이미지 목록 보기
```
docker pull 
```


이미지 목록 보기
```
docker pull 
```


이미지 목록 보기
```
docker pull 
```


이미지 목록 보기
```
docker pull 
```


이미지 목록 보기
```
docker pull 
```


이미지 목록 보기
```
docker pull 
```


이미지 목록 보기
```
docker pull 
```
