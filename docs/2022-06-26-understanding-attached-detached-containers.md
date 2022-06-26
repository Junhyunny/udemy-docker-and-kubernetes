## Understanding attached and detached containers

### 1. docker start 명령어 실행

* `docker start` 명령어로 컨테이너를 재실행하면 컨테이너는 백그라운드에서 동작한다. 
* 별도로 동작 중인 로그로 연결되지 않고, 어떤 컨테이너를 실행했는지 로그만 출력된 후 다시 터미널로 돌아온다.

```
$ docker ps -a
CONTAINER ID   IMAGE                COMMAND                  CREATED              STATUS                      PORTS                  NAMES
c90933464505   d39f5e005627         "/docker-entrypoint.…"   About a minute ago   Exited (0) 32 seconds ago                          nice_mcclintock
f62a53cf5186   react-app-prod:0.1   "/docker-entrypoint.…"   5 hours ago          Up 5 hours                  0.0.0.0:8081->80/tcp   lucid_dirac
8907355ca6fa   react-app-dev:0.1    "/docker-entrypoint.…"   5 hours ago          Up 5 hours                  0.0.0.0:8080->80/tcp   focused_golick

$ docker start c90933464505                  
c90933464505
```

### 2. attaced 모드 실행

* 도커 컨테이너 실행 시 별도의 설정이 없다면 어플리케이션이 `foreground`에서 동작한다.

```
$ docker run -p 8083:80 55549a2fee4d
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: /etc/nginx/conf.d/default.conf differs from the packaged version
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
172.17.0.1 - - [26/Jun/2022:13:27:17 +0000] "GET / HTTP/1.1" 200 644 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:101.0) Gecko/20100101 Firefox/101.0" "-"
172.17.0.1 - - [26/Jun/2022:13:27:17 +0000] "GET /static/js/main.66ccad18.js HTTP/1.1" 200 144060 "http://localhost:8083/" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:101.0) Gecko/20100101 Firefox/101.0" "-"
172.17.0.1 - - [26/Jun/2022:13:27:17 +0000] "GET /static/css/main.073c9b0a.css HTTP/1.1" 200 1044 "http://localhost:8083/" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:101.0) Gecko/20100101 Firefox/101.0" "-"
172.17.0.1 - - [26/Jun/2022:13:27:17 +0000] "GET /static/media/logo.6ce24c58023cc2f8fd88fe9d219db6c6.svg HTTP/1.1" 200 2632 "http://localhost:8083/" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:101.0) Gecko/20100101 Firefox/101.0" "-"
172.17.0.1 - - [26/Jun/2022:13:27:17 +0000] "GET /favicon.ico HTTP/1.1" 200 3870 "http://localhost:8083/" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:101.0) Gecko/20100101 Firefox/101.0" "-"
172.17.0.1 - - [26/Jun/2022:13:27:17 +0000] "GET /logo192.png HTTP/1.1" 200 5347 "http://localhost:8083/" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:101.0) Gecko/20100101 Firefox/101.0" "-"
```

### 3. detached 모드 실행

* `-d` 옵션을 통해 detaced 모드로 컨테이너를 실행할 수 있다.

```
$ docker run -p 8083:80 -d 55549a2fee4d
32a8d3a2d74009339985235c872c183161e0c38491bb8fce2ec5a2222a657c80
```

### 4. attach 명령어

* `attach` 명령어를 사용하면 detached 모드의 컨테이너에 접근할 수 있다.

```
$ docker ps   
CONTAINER ID   IMAGE                COMMAND                  CREATED         STATUS         PORTS                  NAMES
d6f414b858ca   55549a2fee4d         "/docker-entrypoint.…"   8 seconds ago   Up 7 seconds   0.0.0.0:8083->80/tcp   pedantic_stonebraker
f62a53cf5186   react-app-prod:0.1   "/docker-entrypoint.…"   8 hours ago     Up 8 hours     0.0.0.0:8081->80/tcp   lucid_dirac
8907355ca6fa   react-app-dev:0.1    "/docker-entrypoint.…"   8 hours ago     Up 8 hours     0.0.0.0:8080->80/tcp   focused_golick

$ docker attach d6f414b858ca            
172.17.0.1 - - [26/Jun/2022:16:05:56 +0000] "GET / HTTP/1.1" 304 0 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:101.0) Gecko/20100101 Firefox/101.0" "-"
172.17.0.1 - - [26/Jun/2022:16:05:57 +0000] "GET / HTTP/1.1" 304 0 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:101.0) Gecko/20100101 Firefox/101.0" "-"
```

### 5. start 명령어

* `start` 명령어를 사용하면 정지 중인 컨테이너를 재실행할 수 있다.
* 기본적으로 detaced 모드로 컨테이너를 실행한다.
* `-a` 옵션을 사용하면 attached 모드로 어플리케이션을 실행할 수 있다.

```
$ docker start pedantic_stonebraker            
pedantic_stonebraker

$ docker start -a pedantic_stonebraker
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: /etc/nginx/conf.d/default.conf differs from the packaged version
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
172.17.0.1 - - [26/Jun/2022:16:14:08 +0000] "GET / HTTP/1.1" 304 0 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:101.0) Gecko/20100101 Firefox/101.0" "-"
172.17.0.1 - - [26/Jun/2022:16:14:09 +0000] "GET / HTTP/1.1" 304 0 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:101.0) Gecko/20100101 Firefox/101.0" "-"
```

### 6. log 명령어

* `log` 명령어를 사용하면 컨테이너의 로그를 확인할 수 있다.
* 기본적으로 어플리케이션의 로그를 1회 확인한다.
* `-f` 옵션을 사용하면 로그를 1회 확인하고 종료하는 것이 아니라 실시간으로 로그를 확인한다.

```
$ docker logs -f pedantic_stonebraker 
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: /etc/nginx/conf.d/default.conf differs from the packaged version
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
172.17.0.1 - - [26/Jun/2022:16:05:56 +0000] "GET / HTTP/1.1" 304 0 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:101.0) Gecko/20100101 Firefox/101.0" "-"
172.17.0.1 - - [26/Jun/2022:16:05:57 +0000] "GET / HTTP/1.1" 304 0 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:101.0) Gecko/20100101 Firefox/101.0" "-"
```