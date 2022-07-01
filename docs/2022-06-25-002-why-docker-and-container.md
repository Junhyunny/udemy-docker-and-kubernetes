
## Why Docker and Containers?

### 1. 컨테이너가 필요한 이유

* 컨테이너는 독립적이고 표준화 된 어플리케이션 패키지이다.
* 왜 독립적이고, 표준화 된 어플리케이션 패키지가 필요한가?
    * 개발 환경과 배포 환경은 다르다.
    * 어플리케이션의 구축, 테스트, 실행을 모두 같은 환경에서 진행해야 한다.
        * 예를 들어 로컬 호스트에선 Node.js 14 버전을 사용하고, 원격 서버에선 Node.js 12 버전을 사용하는 경우 배포하는 시점에 문제가 발생한다. 
    * 협업하는 경우 서로 다른 팀에서 일하는 경우 문제가 발생하므로 이를 해결해야 한다.
    * 서로 다른 프로젝트에서 버전 충돌이 발생하므로 이를 해결해야 한다.