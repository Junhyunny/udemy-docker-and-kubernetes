## Using Docker Compose for Utility Image

### 1. Dockerfile 

```dockerfile
FROM node:14-alpine

WORKDIR /app

ENTRYPOINT [ "npm" ]
```

### 2. docker-compose.yml

* stdin_open - 사용자 입력을 받을 수 있도록 설정
* tty - 터미널로 사용자 입력 

```yml
version: '3.8'
services:
  npm: 
    build: ./
    stdin_open: true
    tty: true
    volumes:
      - ./:/app
```

### 3. docker-compose run 명령어

* 해당 명령어를 사용하면 docker-compose.yml 파일 내 하나의 서비스만 실행 가능하다.
* 이를 이용하여 docker-compose.yml 파일 내부의 유틸 성격의 이미지를 사용한다.
* 해당 명령어는 자동으로 컨테이너를 삭제하지 않으므로 `--rm` 옵션을 함께 사용한다.

```
$ docker-compose run --rm npm install express -dev
```