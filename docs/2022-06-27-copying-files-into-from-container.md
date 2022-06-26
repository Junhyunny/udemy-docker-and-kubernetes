## Copying files into and from a container

### 1. docker cp 명령어

* 실행 중인 컨테이너로부터 파일을 복사
* 실행 중인 컨테이너에게 파일을 복사
* /projects/2022-06-27-copy-dummy-file 프로젝트 참고
    * 이미지 `7937194bef2c`를 컨테이너로 실행
    * 컨테이너 `distracted_varahamihira`의 test 폴더에 dummy 폴더 복사
    * 컨테이너 `distracted_varahamihira`의 test 폴더를 해당 test 폴더에 복사

```
$ ls
Dockerfile   dummy        package.json public       server.js

$ docker images
REPOSITORY   TAG       IMAGE ID       CREATED              SIZE
<none>       <none>    7937194bef2c   56 seconds ago       923MB
<none>       <none>    96787c4ab7a3   About a minute ago   923MB
<none>       <none>    701a360a8f3c   29 minutes ago       1GB

$ docker run -d -p 3000:80 7937194bef2c
6fff10bbc8ed3b531dba4bcce946bf0eb84b1da33852ff57e51b906ff11b692a

$ docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS          PORTS                  NAMES
6fff10bbc8ed   7937194bef2c   "docker-entrypoint.s…"   2 seconds ago    Up 2 seconds    0.0.0.0:3000->80/tcp   distracted_varahamihira
2f8ab8cd388d   701a360a8f3c   "docker-entrypoint.s…"   28 minutes ago   Up 28 minutes   0.0.0.0:3030->80/tcp   zen_hypatia

$ docker cp  dummy/. distracted_varahamihira:/test

$ docker cp distracted_varahamihira:/test test

$ ls
Dockerfile   dummy        package.json public       server.js    test
```

### 2. 컨테이너 내부 bash 사용

* docker exec -it [컨테이너] bash

```
$ docker exec -it 6fff10bbc8ed bash           
root@6fff10bbc8ed:/app# cd /test/
root@6fff10bbc8ed:/test# cat dummy.txt 
hello!
root@6fff10bbc8ed:/test# 
```