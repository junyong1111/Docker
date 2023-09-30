2. 컨테이너 이미지

## 이미지

**이미지는 응용프로그램을 실행하는데 필요한 모든 것을 포함하고 있다.**

1. 컨테이너가 시작될 때 명령어
2. 파일 스냅샵
    - 컨테이너가 카톡을 실행하고 싶다면 카톡 실행을 할 때 필요한 파일

<img width="451" alt="1" src="https://github.com/junyong1111/Docker/assets/79856225/16a9081e-e0c3-47d8-9693-14e764f462f1">

### 이미지로 컨테이너 만드는 순서

1. Docker 클라이언트에서 docker run <이미지> 입력

```bash
docker run <이미지>
```

1. Docker 이미지에 있는 파일 스냅샵을 컨테이너 하드 디스크로 옮겨준다.

<img width="1177" alt="2" src="https://github.com/junyong1111/Docker/assets/79856225/25ddaa0e-b6f9-4eaf-a755-33ec4e9621a8">

1. 이미지에서 가지고 있는 명령어를 이용해서 해당 파일을 실행

<img width="1195" alt="3" src="https://github.com/junyong1111/Docker/assets/79856225/ab4a08a0-5816-4c0d-8890-a4181095e542">
