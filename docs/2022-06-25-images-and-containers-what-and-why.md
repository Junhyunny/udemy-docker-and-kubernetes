
## Images and Containers: What and why?

### 1. Container

* 어플리케이션과 실행 환경을 하나로 만든 패키지
* 실행 중인 소프트웨어 단위

### 2. Image

* 컨테이너를 만들기 위한 템플릿(template) 혹은 블루 프린트(blue print)
* 코드, 필요한 도구들, 런타임(runtime)을 포함
    * 예를 들어 NodeJs 환경과 NodeJs 어플리케이션을 이미지로 만들고, 이미지를 사용하여 여러 개의 컨테이너를 실행할 수 있다.
    * 이미지는 한번만 만들고, 컨테이너는 여러 개 실행할 수 있다.