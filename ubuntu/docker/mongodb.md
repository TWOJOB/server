## [도커 이미지](https://hub.docker.com/)



## mongodb설치


1
```
apt-get update && apt-get install
```


2
```
apt-get install wget
```

Y입력

3
```
apt-get install gnupg
```

Y입력

4
```
wget -qO - https://www.mongodb.org/static/pgp/server-5.0.asc | apt-key add -
```


5
```
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/5.0 multiverse" | tee /etc/apt/sources.list.d/mongodb-org-5.0.list
```


6
```
apt-get update
```


7
```
apt-get install -y mongodb-org
```

6(아시아)입력
69(서울)입력

설치확인
```
mongo --version
```
