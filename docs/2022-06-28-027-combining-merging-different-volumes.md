## Combining and merging different volumes

### 1. Understanding container and volume interaction

* `VOLUME`, `BIND MOUNT` 두 종류의 저장소 모두 컨테이너에 올라간다.
* `VOLUME`인 경우 컨테이너의 데이터가 볼륨에 저장된다.
    * 컨테이너가 데이터에 주체이며, 컨테이너가 데이터를 호스트 저장소에 저장한다.
* `BIND MOUNT`인 경우 저장소 데이터에 컨테이너가 접근 가능하다.
    * 호스트(개발자)가 데이터의 주체이며, 호스트가 데이터를 호스트 저장소에 저장하면, 컨테이너가 사용할 수 있다.
    * 도커가 호스트의 데이터를 변경할 수는 없다.

### 2. Bind Mount 시 의존성을 찾지 못하는 현상 해결

* /projects/2022-06-28-data-volumes-03-adj-node-code 프로젝트 참조
* 프로젝트 디렉토리를 컨테이너에게 바인딩 해놓으면 어플리케이션이 필요한 의존성을 찾지 못하는 문제가 발생한다.
* 호스트에 `node_modules`에 필요한 의존성들을 미리 설치한다.
    * 호스트에서 `npm install` 명령어 실행
* 컨테이너에게 특정 경로는 호스트의 저장소를 사용하지 않도록 알려준다.
    * 컨테이너를 실행할 때 `node_modules`는 익명 볼륨을 사용하도록 `-v` 옵션으로 지정한다.
    * Dockerfile에 `node_modules`에 익명 볼륨이 지정되도록 `VOLUME` 명령어를 작성한다. 

```
$ docker run -p 3000:80\
    -d\
    -v feedback:/app/feedback\
    -v "/Users/junhyunk/Desktop/workspace/udemy/udemy-docker-and-kubernetes/projects/2022-06-28-data-volumes-03-adj-node-code":/app\
    -v /app/node_modules\
    --rm\
    --name feedback-app\
    feedback-node:volumes
```