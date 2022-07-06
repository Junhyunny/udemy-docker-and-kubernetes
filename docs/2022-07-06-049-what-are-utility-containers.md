## What are "Utility Containers"?

### 1. Utility Containers

* Application Container는 동작 환경과 어플리케이션이 함께 이미지로 만들어진다.
* `docker run` 명령어를 통해 컨테이너를 실행하면 Dockerfile의 `CMD` 명령어가 실행되면서 어플리케이션을 실행한다.
* Utility Container는 동작 환경만 묶인 이미지이다. 
* 사용자의 특정 명령어를 실행한다.