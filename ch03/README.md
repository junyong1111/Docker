3. 컨테이너 명령어 및 생명주기

## 컨테이너 명령어

```bash
docker run <이미지 이름> 특정 명령어
```

위와 같은 명령어 입력시 docker run 실행 명령어를 무시하고 특정 명령어를 실행한다.

ex)

```bash
docker run alpine ping localhost #-- alpine 기본 실행 명령어를 무시하고 로컬로 ping을 날림
```

<img width="493" alt="1" src="https://github.com/junyong1111/Docker/assets/79856225/fbbc3f06-0019-44f9-86fd-9d8a39dc389c">


### 1. 2개의 터미널 실행

- 1개는 컨테이너 실행
- 1개는 docker ps로 실행준인 컨테이너 나열

<img width="1643" alt="2" src="https://github.com/junyong1111/Docker/assets/79856225/9286db33-c8ac-4be5-bbc3-d541a727dc63">

### 2. 컨테이너 Ps 상세 설명

**CONTAINER ID** 

- 컨테이너의 고유 해쉬값 ID 실제로는 더 길지만 일부만 표시

**IMAGE**

- 컨테이너 생성시 사용한 도커 이미지

 **COMMAND**

- 컨테이너 시작시 실행될 명령어
- 대부분 이미지에 내장되어 있으므로 별도 설정 X

 **CREATED**

- 컨테이너가 생성된 시간

 **STATUS**

- 컨테이너의 상태
    - 실행 중 : UP
    - 종료 : Exited
    - 일시정지 : Pause

**PORTS**

- 컨테이너가 개방한 포트와 호스트에 연결한 포트
- 특별한 설정을 하지 않은 경우 표시되지 않음

**NAMES**

- 컨테이너의 고유한 이름
- 컨테이너 생성 시 —name 옵션으로 설정 가능
- 도커 엔진이 임의로 설정함

### 3. 원하는 포멧만 보기

- 이미지와 이름 포멧만 보기

```bash
docker ps --format 'table{{.Names}}\table{{.Image}}'
```

### 4. 실행중이지 않은 모든 컨테이너 보기

```bash
docker ps -a
```

## 컨테이너 생명주기

<img width="1385" alt="3" src="https://github.com/junyong1111/Docker/assets/79856225/2bee26aa-c389-4440-b498-e493f2c5c487">

<img width="1046" alt="4" src="https://github.com/junyong1111/Docker/assets/79856225/09114f63-7ccd-4165-ab6f-fda5dd765986">

**모든 도커 컨테이너 (네트워크 포함) 삭제**

- 현재 실행중인 컨테이너에는 영향이 없다.

```bash
docker system prune
```

## 실행중인 컨테이너 명령어 실행

1. 컨테이너 실행

```bash
docker run alpine ping localhost #-- alpine 기본 실행 명령어를 무시하고 로컬로 ping을 날림
```

<img width="769" alt="5" src="https://github.com/junyong1111/Docker/assets/79856225/bc5c18fc-a15b-4e0e-937b-a8ed2cf4b0bd">


1. 컨테이너 ID 추출

```bash
docker ps
```

<img width="1029" alt="6" src="https://github.com/junyong1111/Docker/assets/79856225/5aec6847-042b-425f-9908-a14eea3cc571">

1. 실행중인 컨테이너 명령어 실행

```bash
docker exec <컨테이너ID> <실행할 명령어>
```

<img width="833" alt="7" src="https://github.com/junyong1111/Docker/assets/79856225/488dcad2-a2a1-4c75-a5f3-883d6d3da44c">