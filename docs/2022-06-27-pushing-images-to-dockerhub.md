## Pushing images to docker hub

### 1. 도커 이미지 저장소

* Docker hub
    * 공식 도커 이미지 저장소
    * 무료로 사용 가능
    * 추가적인 기능이 필요한 경우 유료 솔루션 사용 가능
    * 공식적인 버전의 이미지들이 저장된 장소
* Private Registry
    * 비공개 도커 이미지 저장소
    * 팀끼리 사용하는 저장소

### 2. docker push 명령어

* `docker push [이미지_이름]` 명령어를 통해 이미지를 저장소에 업로드할 수 있다.
* `이미지_이름`에 저장소의 호스트 정보를 추가할 수 있다.
    * HOST:NAME
* 도커 허브에 저장소를 만든 후 테스트를 진행합니다.

```
$ docker push opop3966/hello-world:0.1
The push refers to repository [docker.io/opop3966/hello-world]
a51e560af660: Pushed 
c28c5e308259: Pushed 
203cfb26d843: Pushed 
6491180db8d2: Pushed 
586c0b414da7: Mounted from library/node 
0bfd290f2c17: Mounted from library/node 
6d75cd01c26c: Mounted from library/node 
95904c181913: Mounted from library/node 
df69bfa94785: Mounted from library/node 
f35deb8d96fc: Mounted from library/node 
f6c2459e2059: Mounted from library/node 
f8323fb3a55c: Mounted from library/node 
2f4dc9775f33: Mounted from library/node 
0.1: digest: sha256:acec5bcb63b1785e035156d0890e42ea62553e02481414a8fae4a9de9b5009c0 size: 3048
```

<img src="../images/pushing-images-to-dockerhub-1.png" width="80%" />

### 3. docker pull 명령어

* `docker pull [이미지_이름]` 명령어를 통해 이미지를 저장소에서 다운받을 수 있다.
* `이미지_이름`에 저장소의 호스트 정보를 추가할 수 있다.
    * HOST:NAME

```
$ docker images
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE

$ docker pull opop3966/hello-world:0.1
0.1: Pulling from opop3966/hello-world
f5196cdf2518: Already exists 
9bed1e86f01e: Already exists 
f44e4bdb3a6c: Already exists 
2f75d131f406: Already exists 
07dff4ad21eb: Already exists 
e0ac4f13b766: Already exists 
df2c3b2eb7cc: Already exists 
efe636eac583: Already exists 
fe17849545bb: Already exists 
4eaf0f17453e: Already exists 
111fc5d02764: Already exists 
e005bdfcbc38: Already exists 
cc558b31886e: Already exists 
Digest: sha256:acec5bcb63b1785e035156d0890e42ea62553e02481414a8fae4a9de9b5009c0
Status: Downloaded newer image for opop3966/hello-world:0.1
docker.io/opop3966/hello-world:0.1

$ docker images
REPOSITORY             TAG       IMAGE ID       CREATED             SIZE
opop3966/hello-world   0.1       7937194bef2c   About an hour ago   923MB
```

### 4. docker tag 명령어

* 도커 이미지 이름을 변경할 수 있는 명령어
* docker tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG]

```
$ docker images
REPOSITORY       TAG       IMAGE ID       CREATED             SIZE
hello-world      0.1       610885e2a0f7   42 minutes ago      923MB
my-node-server   0.1       610885e2a0f7   42 minutes ago      923MB
<none>           <none>    7937194bef2c   About an hour ago   923MB

$ docker tag 7937194bef2c opop3966/hello-world:0.1

$ docker images
REPOSITORY             TAG       IMAGE ID       CREATED             SIZE
hello-world            0.1       610885e2a0f7   42 minutes ago      923MB
my-node-server         0.1       610885e2a0f7   42 minutes ago      923MB
opop3966/hello-world   0.1       7937194bef2c   About an hour ago   923MB
```