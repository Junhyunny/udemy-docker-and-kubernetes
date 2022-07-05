## Docker Compose: What and Why?

### 1. What is Docker Compose?

* `docker build`, `docker run` 명령어를 한번에 사용할 수 있는 방법
* 하나의 configuration 파일을 사용한다.
* Orchestration Command(build, start, stop ...)를 사용해서 모든 서비스들과 컨테이너들을 한번에 실행, 종료한다.
* Docker Compose is NOT
    * Docker Compose는 Dockerfile을 대체하지 않는다.
    * Docker Compose는 이미지나 컨테이너들을 대체하지 않는다.
    * Docker Compose는 다중 컨테이너들을 다른 호스트(host or machines)에서 관리하는데 적합하지 않다.
* Docker Compose 파일을 만들어야 한다.
* Docker Compose 파일에는 다음과 같은 내용들이 추가된다.
    * published ports
    * environment variables
    * volumes
    * networks
