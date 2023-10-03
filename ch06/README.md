6. 실제 앱을 이용하여 도커 사용

Python Django앱을 이용하여 도커 사용

## Django-dockerapp 폴더 생성

## 1. Django 프로젝트 생성

[Full Stack Project with Django](https://www.notion.so/Full-Stack-Project-with-Django-2b6b582bff08443da3145262af475d28?pvs=21) 

```bash
django-admin startproject django_docker
```

## 2. Docker 파일 작성하기

1. 이미지 생성 
2. 이미지를 이용하여 컨테이너 실행
3. 컨테이너 안에서 Django 앱 실행

**이미지 생성을 위한 도커 파일 작성**

- 해당 프로젝트 폴더에 dockerfile 생성

```bash
#-- 베이스 이미지를 명시
FROM python:3.9
#-- 추가적으로 필요한 파일들을 다운로드
RUN pip install django==4.0
#-- 컨테이너 시작시 실행될 명령어
CMD ["python", "manage.py", "runserver" ]
```

- COPY 명령어를 통해서 필요한 모든 파일을 카피해줘야 함
    
    <img width="615" alt="1" src="https://github.com/junyong1111/Docker/assets/79856225/c023748b-35cf-409f-b23a-d771c8c33bab">
    

```bash
#-- 베이스 이미지를 명시
FROM python:3.9

#-- 추가적으로 필요한 파일들을 다운로드
RUN pip install django==4.0

#-- 소스 코드 복사
COPY ./ ./

#-- 컨테이너 시작시 실행될 명령어
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000", "--noreload"]

#-- 포트 설정
EXPOSE 8000
```

- **docker run을 이용하여 컨테이너에서 장고앱 실행**

<img width="767" alt="2" src="https://github.com/junyong1111/Docker/assets/79856225/7cc69206-cda7-4c84-aab2-edb154189288">


**네트워크 또한 로컬 네트워크를 복사해줘야 접근이 가능하다.**

- 이 과정에서 src →dst 네트워크 포트 번호간의 매핑을 해야함
- src → 내가 접근하려는 포트
- dst → 컨테이너 포트 번호
    - **즉 8000:8000 으로 매핑하면 자신의 네트워크 포트에서 컨테이너 8000포트번호로 매핑이 된다.**

<img width="926" alt="3" src="https://github.com/junyong1111/Docker/assets/79856225/561d28ee-20fd-4a8b-88ea-5656c069f3d2">

<img width="935" alt="4" src="https://github.com/junyong1111/Docker/assets/79856225/9474f58e-03e2-4a72-8d9d-8dfb55befd42">

```bash
docker run -p 8000 : 8000 <자신의 컨테이너 ID>
```

<img width="1073" alt="5" src="https://github.com/junyong1111/Docker/assets/79856225/d1ec0225-e0e9-4ef1-bd5a-0bcaa4982c56">


[localhost:8000](http://localhost:8000) 위 주소로 접속하면 잘 나온다!!

# 도커 워킹디렉토리 설정

기존 도커 이미지는 필요한 디렉토리만 포함되어 있지만 이전에 만든 도커 이미지에서는 정리가 안되어 있으므로 잠재적인 위험이 존재한다.

- 정리가 잘 된 디렉토리
    
    <img width="453" alt="6" src="https://github.com/junyong1111/Docker/assets/79856225/c0256590-dc0a-48b7-9551-a7b7896f5c51">
    
- 정리가 안된 디렉토리
    
    <img width="483" alt="7" src="https://github.com/junyong1111/Docker/assets/79856225/7cd0a84f-ece8-477c-81c2-a62a3fbb4539">

    
    ```bash
    docker run -it <자신의 이미지 ID> ls
    ```
    
    위 명령어를 통해 정리가 안된 디렉토리를 확인할 수 있음
    

- 워킹디렉토리 설정
    
    ```bash
    #-- 베이스 이미지를 명시
    FROM python:3.9
    
    #-- 추가적으로 필요한 파일들을 다운로드
    RUN pip install django==4.0
    
    #-- WORKDIR 설정 
    WORKDIR /my/app
    
    #-- 소스 코드 복사
    COPY ./ ./
    
    #-- 컨테이너 시작시 실행될 명령어
    CMD ["python", "manage.py", "runserver", "0.0.0.0:8000", "--noreload"]
    
    #-- 포트 설정
    EXPOSE 8000
    ```
    

이미지 재빌드 후 디렉토리 확인

<img width="481" alt="8" src="https://github.com/junyong1111/Docker/assets/79856225/55297f76-65b7-483b-8a70-46923509e462">

**워킹 디렉토리를 설정하면 컨테이너 접근 시 루트부터 접근하는게 아닌 워킹 디렉토리부터 접근한다.**

<img width="580" alt="9" src="https://github.com/junyong1111/Docker/assets/79856225/8a7d8e70-87a7-4511-8ba9-c22ea36b5c90">
