아나콘다에
```
conda create -n yolov8 python=3.9
```
입력후 Y



가상환경 접속
```
conda activate yolov8
```

```
pip install ultralytics
```

파이썬 실행
```
python
```


```
import torch
```

```
torch.cuda.is_available()
```
결과가 False일 경우 토치 설치

버전 확인
```
torch.__version__
```

나가기
```
exit()
```

버전 확인 후
[파이토치](https://pytorch.kr/get-started/locally/) 접속 후
Stable, Windows, pip, python, CUDA 11.7 클릭 후 아래 명령어 복사

```
pip3 install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu117
```

입력




