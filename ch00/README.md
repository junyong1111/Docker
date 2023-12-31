# Docker

### **도커의 필요성**

도커의 사용 이유를 이유하기 위해서는 개발팀과 운영팀간에 관계에 대해 알아야 한다.

**개발팀과 운영팀은 적대적이면 안된다.**

도커는 개발팀과 운영팀 사이에서 협업과 애플리케이션 배포를 효율적으로 관리하는 데 도움이 된다. 개발팀과 운영팀 사이의 조화로운 협력은 전체 소프트웨어 개발 및 운영 라이프사이클에서 중요하다.

**개발팀의 관점에서 도커의 사용 이유**

1. **새로운 기능 개발 및 테스트:** 도커를 사용하면 개발팀은 어플리케이션을 격리된 환경인 컨테이너 내에 패키징하여 개발하고, 이를 빠르게 테스트하고 배포할 수 있다. 이로 인해 빠른 개발과 배포 주기를 갖을 수 있다.
2. **환경 일관성:** 각 개발자가 원하는 언어와 도구를 사용하여 애플리케이션을 개발할 수 있다. 개발팀은 도커 이미지를 통해 표준화된 환경을 갖추며, 이를 개발 환경에서 운영 환경까지 일관성 있게 유지할 수 있다.
3. **이식성과 확장성:** 도커를 사용하면 애플리케이션과 종속성을 모두 포함한 컨테이너를 만들어 배포할 수 있다. 이로 인해 다양한 환경에서 애플리케이션을 실행하고 쉽게 확장할 수 있다.

**운영팀의 관점에서 도커의 사용 이유:**

1. **안정성과 격리:** 도커 컨테이너는 애플리케이션을 격리된 환경으로 실행하므로, 운영팀은 서로 다른 애플리케이션이 서로 영향을 미치지 않도록 안정적인 운영 환경을 유지할 수 있다.
2. **자원 효율성:** 가상 머신과 비교하여 도커 컨테이너는 더 가볍고 빠르게 시작하며 자원을 효율적으로 사용한다. 따라서 더 많은 애플리케이션을 동일한 하드웨어 리소스로 실행할 수 있다.
3. **스케일링과 자동화:** 도커는 자동화된 배포와 스케일링을 지원하여 운영팀은 쉽게 애플리케이션을 확장하고 관리할 수 있다.

**VM과 도커의 비교:**

VM은 하이퍼바이저를 통해 각각의 가상 머신 안에 운영 체제를 설치하는 방식이므로 무겁고 자원 소모가 크다. 반면, 도커는 호스트 운영 체제 위에 컨테이너를 실행하므로 가볍고 빠르며 자원을 효율적으로 사용한다. 따라서 **도커는 더 빠르고 경제적인 가상화 기술이**다.

요약하면 도커는 개발과 운영팀 간의 적절한 협업을 가능케 하는 가상화 기술로서, 애플리케이션의 이식성과 확장성을 높여 전체적인 개발-운영 프로세스를 효율적으로 관리할 수 있도록 도와준다.

![1](https://github.com/junyong1111/Docker/assets/79856225/1ef5a912-1635-4313-9784-7aa6241a649c)

### 도커

- 컨테이너 기술을 지원하는 다양한 프로젝트 중에 하나
- 컨테이너 기술은 이전에도 있었으나 도커로 인해 알려짐
- 컨테이너 기술의 사실상 표준
- 다양한 운영체제에서 사용 가능(리눅스, 윈도우, MacOS)
- 리눅스의 네임 스페이스와 cgroups와 같은 커널 기능을 사용하여 가상화
- 애플리케이션에 국한 되지 않고 의존성 및 파일 시스템까지 패키징하여 빌드, 배포, 실행을 단순화
    
    <img width="582" alt="2" src="https://github.com/junyong1111/Docker/assets/79856225/dc1fc60b-bd82-4bb3-a1fa-b8eb37ba018d">
    

- **클라우드 컴퓨팅 서비스 모델**
1. **IaaS (Infrastructure as a Service - 인프라스트럭처 서비스):**
    - 가상 머신, 네트워크, 스토리지와 같은 기본적인 인프라 자원을 제공하는 서비스 모델
    - 사용자는 가상 머신을 만들고, 운영 체제를 설치하고, 원하는 소프트웨어를 설치하여 컴퓨팅 리소스를 관리할 수 있다.
    - 사용자는 하드웨어와 인프라를 관리하고 운영하는 책임이 있다.
    - 예시: Amazon EC2, Microsoft Azure Virtual Machines
2. **PaaS (Platform as a Service - 플랫폼 서비스):**
    - 응용 프로그램 개발 및 배포를 위한 플랫폼을 제공하는 서비스 모델
    - 사용자는 애플리케이션을 개발하기 위한 프로그래밍 언어, 런타임, 데이터베이스 등의 플랫폼을 사용할 수 있다.
    - 인프라에 대한 걱정 없이 애플리케이션 개발과 배포에만 집중할 수 있다.
    - 예시: Heroku, Google App Engine, Microsoft Azure App Service
3. **SaaS (Software as a Service - 소프트웨어 서비스):**
    - 소프트웨어 애플리케이션을 인터넷을 통해 제공하는 서비스 모델
    - 사용자는 인터넷 브라우저를 통해 해당 소프트웨어에 접속하여 사용할 수 있으며, 모든 관리와 유지 보수는 제공 업체가 담당
    - 사용자는 애플리케이션을 실행하기 위해 별도의 설치나 설정을 필요로 하지 않는다.
    - 예시: Gmail, Dropbox, Salesforce

<img width="537" alt="3" src="https://github.com/junyong1111/Docker/assets/79856225/1ae5e608-e76f-480b-93eb-a0e0f2f581bf">

요약하면, IaaS는 기본적인 인프라 자원을 제공하고, PaaS는 애플리케이션 개발과 배포를 위한 플랫폼을 제공하며, SaaS는 인터넷을 통해 소프트웨어를 제공하는 서비스 모델이다.

- **도커의 이미지  개념**
    - 도커의 이미지는 애플리케이션과 필요한 모든 구성 요소를 포함하는 템플릿이라고 생각할 수 있다. 간단히 말하면, 이미지는 애플리케이션을 실행하는 데 필요한 모든 것들이 미리 묶여 있는 "패키지"이다.
- **컨테이너를 격리하는 기술**
    - **리눅스 네임 스페이스**를 이용하여 이름 공간에 따라 독립적으로 뷰를 제공
        
        <img width="470" alt="4" src="https://github.com/junyong1111/Docker/assets/79856225/10727d15-82e6-4b81-b2fc-7de59be205a3">
        
    - 리눅스 컨트롤 그룰
        - 그룹에 대한 리소스 사용량을 제한하고 제어하는 기술이다. 컨트롤 그룹은 리눅스 커널의 기능 중 하나로서, 여러 프로세스를 그룹으로 묶어서 자원의 할당과 사용을 관리하는데 사용한다.
        
        <img width="596" alt="5" src="https://github.com/junyong1111/Docker/assets/79856225/7dc7c8d5-4847-4d2d-b1a2-0e73118457ad">
