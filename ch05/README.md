5. 도커 이미지 만들기

<img width="832" alt="1" src="https://github.com/junyong1111/Docker/assets/79856225/383f59c4-14f3-4d9b-823f-925d094a8569">

# Hello 문구 출력 이미지 생성

## 1. 도커 파일 작성

- 도커 이미지를 만들기위한 설정 파일이며 컨테이너가 어떻게 행동해야 하는지에 대해 설정하는 파일

### 도커 파일 생성 순서

1. 베이스 이미지를 명시해준다(파일 스냅샷)
2. 추가적으로 필요한 파일을 다운로드 하기 위한 몇가지 명령어를 명시해준다.(파일 스냅샷)
3. 컨테이너 시작시 실행 될 명령어를 명시해준다(컨테이너 시작 명령어)

<img width="873" alt="2" src="https://github.com/junyong1111/Docker/assets/79856225/ff73ac5d-4c28-4763-8aef-b600f2c0ee33">

<img width="462" alt="3" src="https://github.com/junyong1111/Docker/assets/79856225/996b8628-4713-4c77-b728-5925c77829a9">

- 도커 파일을 만들 폴더 생성
- vscode를 사용하여 해당 폴더를 선택
- dockerfile 파일 생성
- 코드 작성(기본 포멧)

```bash
#-- 베이스 이미지를 명시
FROM baseImage
#-- 추가적으로 필요한 파일들을 다운로드
RUN command
#-- 컨테이너 시작시 실행될 명령어
CMD [ "executable" ]
```

<img width="717" alt="4" src="https://github.com/junyong1111/Docker/assets/79856225/a8715606-e9f7-4e4f-b5e3-8615b18bb570">


<img width="993" alt="5" src="https://github.com/junyong1111/Docker/assets/79856225/4ec8984e-4284-4171-9c9e-fa34d45fe800">

## 2. **생성한 도커파일을 도커 클라이언트로 보내기 위해 빌드 명령**

<img width="869" alt="6" src="https://github.com/junyong1111/Docker/assets/79856225/6c35acce-06f7-4ae4-8656-2c349a90140e">


```bash
#-- dockerfile이 있는 working directory에서 다음 명령어 실행
docker build ./
```

<img width="1265" alt="7" src="https://github.com/junyong1111/Docker/assets/79856225/79d5b1bf-d784-4068-8281-a699a9b5269c">

<img width="1010" alt="8" src="https://github.com/junyong1111/Docker/assets/79856225/06c49f5f-fd64-4f56-a7af-c8d068e1dfad">


## 3. Docker Run 실행

<img width="961" alt="9" src="https://github.com/junyong1111/Docker/assets/79856225/f26ba29a-5fbf-4411-8b2c-5d7ebc83b07b">


**위와 같이 컨테이너 id로 실행하면 너무 복잡함 t옵션을 통해 이미지 이름을 줄 수 있음**

<img width="1255" alt="10" src="https://github.com/junyong1111/Docker/assets/79856225/32c0b9f0-ab19-4821-b98e-3f5c16f04d27">


기본적으로 위와같은 방식으로 이름을 지어주는게 암묵적(컨테이너 아이디가 아닌 도커 아이디)

```bash
#-- dockerfile이 있는 working directory에서 다음 명령어 실행
docker build -t jyporse/hello:latest ./
```

<img width="936" alt="11" src="https://github.com/junyong1111/Docker/assets/79856225/2a308b84-75ef-4477-a8ac-a17f5b85f708">


```bash
docker run jyporse/hello
```

<img width="495" alt="12" src="https://github.com/junyong1111/Docker/assets/79856225/3f1e048a-8576-4dce-8c9d-981ff104d0c1">

