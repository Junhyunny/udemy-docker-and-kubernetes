## Deleting images and containers

### 1. docker stop 명령어

* 실행 중인 컨테이너를 정지하는 명령어
* docker stop [OPTIONS] CONTAINER [CONTAINER...]
    * 컨테이너 아이디 혹은 이름 사용

### 2. docker rm 명령어

* 불필요한 컨테이너 삭제
* 동작 중이지 않은 컨테이너만 삭제 가능

```
$ docker ps -a
CONTAINER ID   IMAGE          COMMAND           CREATED          STATUS                        PORTS     NAMES
b49fefad48b0   0cc94ec7a644   "python rng.py"   26 minutes ago   Exited (0) 26 minutes ago               thirsty_bassi
039f2f477b40   0cc94ec7a644   "python rng.py"   27 minutes ago   Exited (130) 27 minutes ago             peaceful_mcnulty
7ff973975623   0cc94ec7a644   "python rng.py"   33 minutes ago   Exited (0) 29 minutes ago               vibrant_dijkstra

$ docker rm thirsty_bassi
thirsty_bassi

$ docker ps -a
CONTAINER ID   IMAGE          COMMAND           CREATED          STATUS                        PORTS     NAMES
039f2f477b40   0cc94ec7a644   "python rng.py"   27 minutes ago   Exited (130) 27 minutes ago             peaceful_mcnulty
7ff973975623   0cc94ec7a644   "python rng.py"   33 minutes ago   Exited (0) 29 minutes ago               vibrant_dijkstra
```

### 3. docker images 명령어

* 현재 사용 중인 이미지 리스트 확인

```
$ docker images
REPOSITORY   TAG       IMAGE ID       CREATED          SIZE
<none>       <none>    0cc94ec7a644   44 minutes ago   920MB
```

### 4. docker rmi 명령어

* 이미지를 삭제하는 명령어
* 컨테이너로 사용 중이지 않은 이미지만 삭제 가능

```
$ docker rm $(docker ps -aq)
039f2f477b40
7ff973975623

$ docker rmi 0cc94ec7a644
Deleted: sha256:0cc94ec7a6440fd1c6a093bfc3c43b06da6d06ce67f4a46bed6857098a946dd2
```

### 5. docker image prune 명령어

* 사용 중이지 않은 이미지를 삭제

```
$ docker image prune
WARNING! This will remove all dangling images.
Are you sure you want to continue? [y/N] Y
Total reclaimed space: 0B
```
