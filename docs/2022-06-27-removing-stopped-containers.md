## Removing stopped containers

### 1. docker run -rm 옵션

* 컨테이너가 실행 종료되면 자동으로 삭제
* 자주 사용되지 않는 옵션이며 컨테이너가 멈추더라도 재시작할 가능성이 없는 경우에 사용

```
$ docker run -d -p 3031:80 --rm 701a360a8f3c
60396eda471f01101899d3b1a5ce6d2ad6c1eec89373d660378c25fd1de1eb34

$ docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED              STATUS              PORTS                  NAMES
60396eda471f   701a360a8f3c   "docker-entrypoint.s…"   5 seconds ago        Up 4 seconds        0.0.0.0:3031->80/tcp   recursing_edison
2f8ab8cd388d   701a360a8f3c   "docker-entrypoint.s…"   About a minute ago   Up About a minute   0.0.0.0:3030->80/tcp   zen_hypatia

$ docker stop 60396eda471f

$ docker ps -a
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS         PORTS                  NAMES
2f8ab8cd388d   701a360a8f3c   "docker-entrypoint.s…"   2 minutes ago   Up 2 minutes   0.0.0.0:3030->80/tcp   zen_hypatia
```