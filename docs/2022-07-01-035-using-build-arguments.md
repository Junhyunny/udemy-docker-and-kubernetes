## Using build arguments(ARG)

### 1. ARG 설정 사용

* `CMD`는 런타임 명령어
*  `$` 기호를 앞에 붙여서 사용하면 변수처럼 사용 가능
* `ARG` 커맨드는 `npm install` 같은 자원을 많이 소모하는 이미지 레이어 뒤에 위치
* `/projects/2022-07-01-data-volumes-08-args-and-env` 프로젝트 참고

### 2. 옵션으로 빌드 변수 주입

* `--build-arg` 옵션을 통해 `Dockerfile`에 작성한 ARG 변수를 오버라이딩할 수 있다.

```
$ docker build -t feedback-node:web-app --build-arg DEFAULT_PORT=3000 .

$ docker run -p 3000:3000\
    -d\
    -v feedback:/app/feedback\
    -v "/Users/junhyunk/Desktop/workspace/udemy/udemy-docker-and-kubernetes/projects/2022-07-01-data-volumes-08-args-and-env":/app:ro\
    -v /app/node_modules\
    -v /app/temp\
    --rm\
    --name feedback-app\
    feedback-node:web-app
```
