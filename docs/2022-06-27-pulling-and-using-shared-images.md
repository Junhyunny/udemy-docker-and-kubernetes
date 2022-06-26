## Pulling and using shared images

### 1. 이미지 다운받기

* docker pull 명령어를 통해 필요한 이미지를 다운 받는다.

```
$ docker pull academind/node-hello-world
Using default tag: latest
latest: Pulling from academind/node-hello-world
419e7ae5bb1e: Pull complete 
848839e0cd3b: Pull complete 
de30e8b35015: Pull complete 
258fdea6ea48: Pull complete 
ddb75eb7f1e9: Pull complete 
7ec8a0667334: Pull complete 
1a5a0fcc10a7: Pull complete 
7137cb3a58d4: Pull complete 
0725fe303059: Pull complete 
5472ee660c2a: Pull complete 
0e2b696290c3: Pull complete 
9c74de367b21: Pull complete 
be08011511a7: Pull complete 
Digest: sha256:7214ae016bd22c5b1dacfdb8dea50822fe4ec5c365355bf2acc193774cfb412a
Status: Downloaded newer image for academind/node-hello-world:latest
docker.io/academind/node-hello-world:latest

$ docker images
REPOSITORY                   TAG       IMAGE ID       CREATED         SIZE
opop3966/hello-world         0.1       7937194bef2c   2 hours ago     923MB
academind/node-hello-world   latest    aa7906e341fd   22 months ago   946MB
```

### 2. 도커 이미지 실행

* docker run 명령어를 실행 시 로컬에 이미지가 없는 경우 저장소에서 다운받는다.
* 이미지 다운로드가 완료된 후 컨테이너로 실행한다.
* 로컬에 사용했던 이미지가 있다면 해당 이미지가 최신 버전인지 확인하지 않고 사용한다.

```
$ docker run -p 3000:80 -d --name node-server academind/node-hello-world       
Unable to find image 'academind/node-hello-world:latest' locally
latest: Pulling from academind/node-hello-world
419e7ae5bb1e: Pull complete 
848839e0cd3b: Pull complete 
de30e8b35015: Pull complete 
258fdea6ea48: Pull complete 
ddb75eb7f1e9: Pull complete 
7ec8a0667334: Pull complete 
1a5a0fcc10a7: Pull complete 
7137cb3a58d4: Pull complete 
0725fe303059: Pull complete 
5472ee660c2a: Pull complete 
0e2b696290c3: Pull complete 
9c74de367b21: Pull complete 
be08011511a7: Pull complete 
Digest: sha256:7214ae016bd22c5b1dacfdb8dea50822fe4ec5c365355bf2acc193774cfb412a
Status: Downloaded newer image for academind/node-hello-world:latest
e2becd6b329a5056e1e1a487127c10345c52f4ece2335794d76f5e1ab526480b

$ docker images 
REPOSITORY                   TAG       IMAGE ID       CREATED         SIZE
opop3966/hello-world         0.1       7937194bef2c   2 hours ago     923MB
academind/node-hello-world   latest    aa7906e341fd   22 months ago   946MB
```