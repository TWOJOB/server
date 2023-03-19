# 아나콘다 설치 하기


wget https://repo.continuum.io/archive/Anaconda3-2022.10-Linux-x86_64.sh

bash Anaconda3-2022.10-Linux-x86_64.sh






아나콘다 실행
```
source ~/anaconda3/etc/profile.d/conda.sh
```


주피터노트북 외부 접속

1. 방화벽 해제
```
sudo ufw allow 8888
```

2. jupyter notekook 암호 설정
```
jupyter notebook --gen
```


3. jupyter notebook 설정 파이 수성

```
nano ~/.jupyter_notegook_config.py
```
접속 후 control + w를 눌러서 내요 검색


c.NotebookApp.allow_orign = '*' #외부 접속 허용

c.NotebookApp.

c.NotebookApp.

c.NotebookApp.notebook_dir = '작업 경로'

c.NotebookApp.ip = '*'

c.NotebookApp.port = '8888'

c.NotebookApp.password'<해시화된 비밀번호>' # nano ~/.jupyter_notegook_config.json 에서 확인

c.NotebookApp.password_required = True #  비밀번호 사용여부

c.NotebookApp.open_browser = Fales # 서버 Pc에서 자동으로 브라우저가 열리지 않도록 설정


주피터 노트북 실행
```
jupyter notebook
```
