4. Redis를 이용하여 컨테이너 실행

<img width="959" alt="1" src="https://github.com/junyong1111/Docker/assets/79856225/abbb4660-951d-4c42-b96e-22203db971cc">

## Redis는 NoSQL 데이터 베이스

### 1. Redis 서버 실행

- 1번 터미널로 Redis 서버 실행

```bash
docker run redis
```

<img width="656" alt="2" src="https://github.com/junyong1111/Docker/assets/79856225/0cbd88a0-2ed2-4bc9-a2ea-9e5b3ee7ad2f">

### 2. Redis 클라이언트 실행

- 2번 터미널로 Redis 클라이언트 실행
- 하지만 에러 발생

<img width="755" alt="3" src="https://github.com/junyong1111/Docker/assets/79856225/b1ce94d9-4d51-4831-a7a6-6971686ee8b3">

—# 독립된 컨테이너에서 서버가 실행중이므로 연결할 수 없다 

—# 연결하기 위해서는 서버가 실행되는 컨테이너 안에서 클라이언트를 실행해야 함

### 3. 실행중인 컨테이너에 명령어를 사용하여 클라이언트 실행

- ps 명령어를 통해 서버 ID 확인

```bash
docker ps
```

<img width="1036" alt="4" src="https://github.com/junyong1111/Docker/assets/79856225/3ea71e24-dd15-42af-ac9f-858ad8413c1a">

- exec 명령어를 이용해서 레디스 서버 안에서 클라이언트 cli  실행
- 이 때 그냥 실행하면 추가적인 명령어 실행이 불가능하다 추가적인 명령어 실행을 위해서 -it 플래그를 이용
    
    <img width="1122" alt="5" src="https://github.com/junyong1111/Docker/assets/79856225/8209d988-26ad-48bc-b81d-02bae291f512">
    

```bash
docker exec -it <컨테이너 id> redis-cli
```

<img width="841" alt="6" src="https://github.com/junyong1111/Docker/assets/79856225/5926c7b7-cc15-457e-abb9-2013ed1b4025">

<img width="806" alt="7" src="https://github.com/junyong1111/Docker/assets/79856225/e2581441-5507-4200-b14c-225a0f87c381">

### 4. Redis cli를 통해 데이터베이스에 값 저장 후 확인

- 데이터 베이스에 값 저장

```bash
set key1 hello 
```

<img width="882" alt="8" src="https://github.com/junyong1111/Docker/assets/79856225/6d7a00f4-e202-43ca-9b05-73b38a2fd13f">

- 데이터 베이스 값 조회

```bash
get key
```

<img width="279" alt="9" src="https://github.com/junyong1111/Docker/assets/79856225/fdedd46d-5d93-4873-b436-61a67c3d45c9">


## 추가 : 쉘 환경으로 컨테이너 제어하기

<img width="926" alt="10" src="https://github.com/junyong1111/Docker/assets/79856225/1a148197-d149-4565-98dd-878fa53ced7c">

- 컨테이너 실행

```bash
docker run alpine ping localhost
```

- 컨테이너 쉘 환경으로 명령어 전단

```bash
docker exec -it <컨테이너ID> sh
```

—# 사용하는 base 이미지에 따라 zsh, bash powersehll등 이용 가능

- crtl + d 를 이용하여 쉘 환경에서 빠져 나올 수 있음