
## Virtual Machines and Docker Containers

### 1. 가상 머신(Virtual Machine) 환경

* 호스트 운영체제에 가상 운영체제를 올리는 방법
* 가상 머신은 가싱의 컴퓨터를 에뮬레이트(emulate) 한다.
* 라이브러리들과 의존성들, 도구들을 설치하고 그 위에 어플리케이션을 올린다.

### 2. 가상 머신의 한계

* 어플리케이션 별로 가상 머신을 운영하기 때문에 가상 머신을 호스트 운영체제에 올리는 것은 부하를 유발한다.
* CPU, 메모리 낭비가 발생하며 호스트의 전반적인 속도 저하를 유발한다. 

### 3. 가상 머신 장점과 단점

#### 3.1. 장점

* 환경 분리 가능
* 환경 별 구체적인 설정 사용 가능
* 환경 설정들은 공유가 가능하고 재사용이 가능

#### 3.2. 단점

* 가상 머신이 메모리 상에 불필요하게 중복되므로 공간 낭비 발생
* 속도가 느려질 수 있고, 부팅(booting) 시간이 길게 소요
* 다른 컴퓨터 서버로 재생산할 수 있지만, 복잡

### 4. Docker 환경

* 운영체제에 내장된 에뮬레이트 컨테이너 지원이 필요하다.
* 호스트 운영체제에 도커 엔진(도커 런타임)을 설치한다.
* 도커 엔진 위에 컨테이너들을 올린다.
* 컨테이너는 필요한 라이브러리들과 의존성, 도구들과 어플리케이션이 함께 패키징 된다.
* 도커 컨테이너는 도커 파일을 통해 생성할 수 있으며, 파일을 공유하여 필요한 곳에서 컨테이너를 실행할 수 있다.
* 도커 컨테이너는 이미지를 기반으로 만들어지며, 이미지를 공유하여 필요한 곳에서 컨테이너를 실행할 수 있다.

### 5. 도커 컨테이너와 가상 머신의 차이

#### 5.1. 도커 컨테이너

* Low impact on OS, very fast minimal disk space usage
* Sharing, re-building and distribution is easy
* Encapsulate apps/environments instead of "whole machines"

#### 5.2. 가상 머신

* Bigger impact on OS, slower higher disk space usage
* Sharing, re-building and distribution can be challenging
* Encapsulate "whole machines" instead of just apps/environments