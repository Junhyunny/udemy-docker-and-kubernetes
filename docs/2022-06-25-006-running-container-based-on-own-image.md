
## Running a container based on own images

### 1. 도커 이미지 만들기

* 프로젝트 폴더로 이동
* `docker build` 명령어를 통해 이미지 생성

```
$ cd ${project_dir}
$ docker build .
```

### 2. 도커 컨테이너 실행

* 도커 이미지 확인
* 도커 이미지 ID를 사용하여 컨테이너 실행
* `-p` 태그를 통해 호스트의 포트와 컨테이너의 포트를 연결
    * `-p` - publish tag 

```
$ docker images   
REPOSITORY   TAG       IMAGE ID       CREATED          SIZE
<none>       <none>    cff4dc302492   21 minutes ago   1GB
<none>       <none>    b113bb485f03   23 minutes ago   1GB

$ docker run -p 8080:80 cff4dc302492
```

##### 참고 - 도커 파일

* `EXPOSE` 키워드는 선택적으로 사용
* `EXPOSE` 키워드로 노출할 포트를 작성하는 것은 문서화로써 `BEST PRACTICE` 차원에서 작성
* `2022-06-25-nodejs-app-first-dockerfile` 프로젝트 Dockerfile 참고

```dockerfile
FROM node

WORKDIR /app

COPY . /app

RUN npm install

EXPOSE 80

CMD ["node", "server.js"]
```