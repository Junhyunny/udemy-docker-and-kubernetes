## How docker resolves IP

### 1. Understanding docker network IP resolving

* `host.docker.internal`은 호스트의 주소를 나타낸다.
* 동일 네트워크에 있는 경우 컨테이너 이름을 도메인 이름처럼 사용할 수 있다.
* 도커는 컨테이너 이름을 자동적으로 IP로 변경한다.