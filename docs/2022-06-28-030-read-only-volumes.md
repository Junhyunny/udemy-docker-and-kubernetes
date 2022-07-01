## A look at read-only volumes

### 1. Bind Mounts read-only 사용

* 호스트 파일시스템을 공유하여 코드의 변경을 즉시 컨테이너가 반영하도록 구현 가능
* 호스트의 파일시스템을 컨테이너가 `read-only`로 사용하고 싶다면 별도의 태그를 추가한다.
* Bind mount 처리 시 컨테이너 디렉토리 다음에 `:ro` 옵션을 추가한다.

```
$ docker run -p 3000:80\  
    -d\
    -v feedback:/app/feedback\
    -v "/Users/junhyunk/Desktop/workspace/udemy/udemy-docker-and-kubernetes/projects/2022-06-28-data-volumes-04-added-nodemon":/app:ro\
    -v /app/node_modules\
    --rm\
    --name feedback-app\
    feedback-node:volumes
c251cab39fe6fa7f4126999ae4499b1a4feddf80ff8e40e05e6a54f7a1ab488a
```

##### 에러 로그

```
$ docker logs -f feedback-app
TEST
(node:1) UnhandledPromiseRejectionWarning: Error: EROFS: read-only file system, open '/app/temp/aaa.txt'
(Use `node --trace-warnings ...` to show where the warning was created)
(node:1) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). To terminate the node process on unhandled promise rejection, use the CLI flag `--unhandled-rejections=strict` (see https://nodejs.org/api/cli.html#cli_unhandled_rejections_mode). (rejection id: 1)
(node:1) [DEP0018] DeprecationWarning: Unhandled promise rejections are deprecated. In the future, promise rejections that are not handled will terminate the Node.js process with a non-zero exit code.
```

### 2. read-only 파일 시스템 특정 디렉토리 허용

* read-only 옵션으로 프로젝트 전체를 변경 불가능하게 막은 경우 특정 디렉토리만 쓰기를 허용할 수 있다.
    * Dockerfile 이용 - 특정 디렉토리만 익명 볼륨을 매칭
    * `-v` 옵션 사용 - 컨테이너 실행 시 `-v` 옵션을 통해 특정 디렉토리만 익명 볼륨 매칭

##### 도커 파일

```dockerfile
FROM node:14

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

EXPOSE 80

VOLUME [ "/app/temp" ]

CMD [ "npm", "start" ]
```

##### docker run 명령어

```
$ docker run -p 3000:80\
    -d\
    -v feedback:/app/feedback\
    -v "/Users/junhyunk/Desktop/workspace/udemy/udemy-docker-and-kubernetes/projects/2022-06-28-data-volumes-04-added-nodemon":/app:ro\
    -v /app/node_modules\
    -v /app/temp\
    --rm\
    --name feedback-app\
    feedback-node:volumes
```