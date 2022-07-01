## Working with environment variables and ".env" files

### 1. ARGuments variable

* using when build-time
* Dockerfile 내부에서 사용 가능
* CMD 혹은 어플리케이션 코드에서 사용 불가능
* 도커 이미지를 만들 때 `--build-arg` 옵션을 통해 지정할 수 있다.

### 2. ENVironment variable

* using when run-time
* 도커 파일에서도 사용 가능하며 어플리케이션 코드에서 사용 가능
* 도커 파일에서 지정하거나 컨테이너를 실행할 때 `--env` 옵션을 통해 지정할 수 있다. 
* `/projects/2022-07-01-arg-and-env-options` 프로젝트 참고

### 3. 옵션으로 환경 설정 주입

* -e 옵션 - 환경 설정 값을 지정

```
$ docker run -p 3000:8000\
    -d\
    -v feedback:/app/feedback\
    -v "/Users/junhyunk/Desktop/workspace/udemy/udemy-docker-and-kubernetes/projects/2022-07-01-arg-and-env-options":/app:ro\
    -v /app/node_modules\
    -v /app/temp\
    --env PORT=8000\
    --rm\
    --name feedback-app\
    feedback-node:volumes
```

* --env 옵션 - 환경 설정 값을 지정

```
$ docker run -p 3000:8000\
    -d\
    -v feedback:/app/feedback\
    -v "/Users/junhyunk/Desktop/workspace/udemy/udemy-docker-and-kubernetes/projects/2022-07-01-arg-and-env-options":/app:ro\
    -v /app/node_modules\
    -v /app/temp\
    -e PORT=8000\
    --rm\
    --name feedback-app\
    feedback-node:volumes
```

* --env-file 옵션 - 환경 설정 파일 경로를 지정

```
$ docker run -p 3000:3000\
    -d\
    -v feedback:/app/feedback\
    -v "/Users/junhyunk/Desktop/workspace/udemy/udemy-docker-and-kubernetes/projects/2022-07-01-arg-and-env-options":/app:ro\
    -v /app/node_modules\
    -v /app/temp\
    --env-file ./.env\
    --rm\
    --name feedback-app\
    feedback-node:volumes
```