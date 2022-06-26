## Stop and restarting containers

### 1. 도커 실행 중인 컨테이너 확인

* `docker ps` - 실행 중인 컨테이너 확인
* `docker ps -a` - 모든 컨테이너 확인

```
$ docker ps
CONTAINER ID   IMAGE                COMMAND                  CREATED       STATUS       PORTS                  NAMES
f62a53cf5186   react-app-prod:0.1   "/docker-entrypoint.…"   5 hours ago   Up 5 hours   0.0.0.0:8081->80/tcp   lucid_dirac
8907355ca6fa   react-app-dev:0.1    "/docker-entrypoint.…"   5 hours ago   Up 5 hours   0.0.0.0:8080->80/tcp   focused_golick
```

### 2. 도커 컨테이너 실행

* `docker run [OPTIONS] IMAGE [COMMAND] [ARG...]`
    * 이미지를 기반으로 컨테이너 실행
    * 옵션을 통해 컨테이너 실행 방법을 제어한다.
    * 이미지 아이디나 태그를 사용하여 컨테이너를 실행한다.
    * 명령어나 실행 변수를 전달할 수 있다.

```
$ docker images    
REPOSITORY       TAG       IMAGE ID       CREATED       SIZE
react-app-prod   0.1       d39f5e005627   6 hours ago   23.2MB
react-app-dev    0.1       55549a2fee4d   6 hours ago   23.2MB

$ docker run d39f5e005627      
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: /etc/nginx/conf.d/default.conf differs from the packaged version
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
```

### 3. 실행 중이지 않은 컨테이너 재실행

* `docker start [OPTIONS] CONTAINER [CONTAINER...]`
    * 컨테이너 아이디나 이름을 사용할 수 있다.

```
$ docker start --help

Usage:  docker start [OPTIONS] CONTAINER [CONTAINER...]

Start one or more stopped containers

Options:
  -a, --attach               Attach STDOUT/STDERR and forward signals
      --detach-keys string   Override the key sequence for detaching a container
  -i, --interactive          Attach container's STDIN

$ docker ps -a
CONTAINER ID   IMAGE                COMMAND                  CREATED         STATUS                          PORTS                  NAMES
add452c40626   d39f5e005627         "/docker-entrypoint.…"   2 minutes ago   Exited (0) About a minute ago                          fervent_tereshkova
f62a53cf5186   react-app-prod:0.1   "/docker-entrypoint.…"   5 hours ago     Up 5 hours                      0.0.0.0:8081->80/tcp   lucid_dirac
8907355ca6fa   react-app-dev:0.1    "/docker-entrypoint.…"   5 hours ago     Up 5 hours                      0.0.0.0:8080->80/tcp   focused_golick

$ docker start fervent_tereshkova
fervent_tereshkova

$ docker ps                      
CONTAINER ID   IMAGE                COMMAND                  CREATED         STATUS         PORTS                  NAMES
add452c40626   d39f5e005627         "/docker-entrypoint.…"   5 minutes ago   Up 2 minutes   80/tcp                 fervent_tereshkova
f62a53cf5186   react-app-prod:0.1   "/docker-entrypoint.…"   5 hours ago     Up 5 hours     0.0.0.0:8081->80/tcp   lucid_dirac
8907355ca6fa   react-app-dev:0.1    "/docker-entrypoint.…"   5 hours ago     Up 5 hours     0.0.0.0:8080->80/tcp   focused_golick
```