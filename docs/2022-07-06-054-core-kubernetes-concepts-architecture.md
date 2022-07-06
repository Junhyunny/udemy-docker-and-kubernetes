## Core Kubernentes concepts and architecture

### 1. Kubernentes architecture

* Pod(Container)
    * 가장 작은 실행 가능한 단위
    * configuration 파일을 사용해서 만들 수 있는 단위
    * 하나의 실행 컨테이너에 하나의 파드
* Worker Node
    * 어플리케이션 컨테이너들을 실행할 수 있는 환경
    * Worker Node는 머신으로 생각할 수 있다.
    * 가상의 인스턴스(머신)
    * AWS EC2 컨테이너를 Worker Node라고 볼 수 있다.
    * 하나의 Worker Node에서 여러 개의 Pod를 실행할 수 있다.
* Proxy / Config
    * Kubernetes에 의해 설정된다.
    * Network traffic을 관리한다.
    * Worker Node 내부에 Pod들은 프록시를 통해서 외부와 통신한다.
* Master Node
    * The Control Plane - Worker Node들을 관리
    * Master Node는 배포한 모든 Worker Node들을 관리한다.
    * Control Plane 이 외에도 Worker Node를 관리하기 위한 다양한 컴포넌트들이 존재한다.