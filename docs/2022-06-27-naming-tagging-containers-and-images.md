## Naming and tagging containers and images

### 1. 컨테이너 이름 지정

* `--name` 옵션을 사용하여 컨테이너 이름을 지정
    * 컨테이너 실행 시 `node-js-server` 이름 지정
* 컨테이너 실행 시 별도로 이름을 지정하지 않으면 임의의 이름이 지정되기 때문에 컨테이너 관리가 불편

```
$ docker run -p 3001:80 -d --name node-js-server 7937194bef2c
b4bec21f164d6c5df7d47e14e63e8ee1cc5ca2fd665ca2a0f4a4b58a342dc7ba

$ docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS          PORTS                  NAMES
b4bec21f164d   7937194bef2c   "docker-entrypoint.s…"   3 seconds ago    Up 3 seconds    0.0.0.0:3001->80/tcp   node-js-server
6fff10bbc8ed   7937194bef2c   "docker-entrypoint.s…"   30 minutes ago   Up 30 minutes   0.0.0.0:3000->80/tcp   distracted_varahamihira
```

### 2. 이미지 태그 지정

* 이미지 태그는 두 개의 영역으로 구분된다.
    * `name:tag`
    * `name`은 `REPOSITORY`로 표시된다.
    * `name`은 이미지를 그룹 짓는 용도이다.
    * `tag`는 버전 정보를 정의하는 용도이다.
* `name:tag` 형식으로 고유한 버전의 이미지를 생성한다.

```
$ docker build -t my-node-server:0.1 .
[+] Building 2.6s (10/10) FINISHED
 => [internal] load build definition from Dockerfile                                                                    0.0s
 => => transferring dockerfile: 36B                                                                                     0.0s
 => [internal] load .dockerignore                                                                                       0.0s
 => => transferring context: 2B                                                                                         0.0s
 => [internal] load metadata for docker.io/library/node:12                                                              2.5s
 => [1/5] FROM docker.io/library/node:12@sha256:01627afeb110b3054ba4a1405541ca095c8bfca1cb6f2be9479c767a2711879e        0.0s
 => [internal] load build context                                                                                       0.0s
 => => transferring context: 417B                                                                                       0.0s
 => CACHED [2/5] WORKDIR /app                                                                                           0.0s
 => CACHED [3/5] COPY package.json /app                                                                                 0.0s
 => CACHED [4/5] RUN npm install                                                                                        0.0s
 => [5/5] COPY . /app                                                                                                   0.0s
 => exporting to image                                                                                                  0.0s
 => => exporting layers                                                                                                 0.0s
 => => writing image sha256:610885e2a0f77894815e59e71c52b920b7108ce8a5e5363e7846ff630020b888                            0.0s
 => => naming to docker.io/library/my-node-server:0.1

$ docker images
REPOSITORY       TAG       IMAGE ID       CREATED             SIZE
my-node-server   0.1       610885e2a0f7   7 minutes ago       923MB
<none>           <none>    7937194bef2c   41 minutes ago      923MB
<none>           <none>    96787c4ab7a3   42 minutes ago      923MB
<none>           <none>    701a360a8f3c   About an hour ago   1GB
```

### 3. 이미지 태그를 사용한 컨테이너 실행

* 이미지 아이디가 아닌 태그를 사용하여 컨테이너를 실행할 수 있다.

```
$ docker run -p 3002:80 -d --name node-js-server my-node-server:0.1
11733625c6e2426f501522496c23b4043d39314f2ffe373c04287d601e2da8bd

$ docker ps
CONTAINER ID   IMAGE                COMMAND                  CREATED          STATUS          PORTS                  NAMES
11733625c6e2   my-node-server:0.1   "docker-entrypoint.s…"   2 seconds ago    Up 2 seconds    0.0.0.0:3002->80/tcp   node-js-server
6fff10bbc8ed   7937194bef2c         "docker-entrypoint.s…"   43 minutes ago   Up 43 minutes   0.0.0.0:3000->80/tcp   distracted_varahamihira
```