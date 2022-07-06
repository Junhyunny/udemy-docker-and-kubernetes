## Building images and understanding container names

### 1. --build 옵션

* `docker-compose up --build` - 컨테이너를 실행할 때 강제적으로 이미지를 재빌드하도록 만든다.

### 2. docker-compose build

* `docker-compose build` - 이미지를 빌드만 할 때 사용한다.

### 3. 컨테이너 이름

* `docker-compose.yml` 파일의 service 이름은 네트워크 내부에서 사용되는 이름
* 컨테이너 이름을 별도로 지정하고 싶은 경우 `service.${service_name}.container_name` 설정을 사용