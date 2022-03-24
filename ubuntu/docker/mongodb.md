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


3
```
wget -qO - https://www.mongodb.org/static/pgp/server-5.0.asc | apt-key add -
```


4
```
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/5.0 multiverse" | tee /etc/apt/sources.list.d/mongodb-org-5.0.list
```


5
```
apt-get update
```


5
```
apt-get install -y mongodb-org
```

