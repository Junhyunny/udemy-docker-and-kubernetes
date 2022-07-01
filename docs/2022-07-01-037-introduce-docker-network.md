## Introducing docker networks: Elegant container to container

### 1. Creating container networks

* 연결이 필요한 컨테이너들은 하나의 네트워크로 묶어서 사용한다.
* 아래와 같은 명령어를 통해 네트워크를 구성한다.

```
$ docker run --network my_network ...
```

* 도커 네트워크에선 모든 컨테이너치들은 통신할 수 있다.
* IP 정보들이 자동적으로 해석된다.

### 2. Docker network 만들기

* 다음과 같은 명령어를 통해 네트워크를 만들 수 있다.

```
$ docker network create favorites-net
2879ee64486f3bef27b6f898036774d94912a20570c62e0546cd73f49e2b86de

$ docker network ls
NETWORK ID     NAME            DRIVER    SCOPE
41738f182287   bridge          bridge    local
2879ee64486f   favorites-net   bridge    local
969819b69df5   host            host      local
2e7d396ba961   none            null      local
```

### 3. Docker network 사용하기

* 아래와 같은 명령어를 통해 mongodb 컨테이너를 favorites-net 네트워크에 연결시킨다.

```
$ docker run -d --network favorites-net --name mongodb mongo
$ docker run -d -p 3000:3000 --name network-app --rm --network favorites-net network-app

$ docker ps -a
CONTAINER ID   IMAGE         COMMAND                  CREATED         STATUS         PORTS                    NAMES
872564e10e28   network-app   "docker-entrypoint.s…"   3 seconds ago   Up 2 seconds   0.0.0.0:3000->3000/tcp   network-app
ccd4c8b04d74   mongo         "docker-entrypoint.s…"   5 minutes ago   Up 5 minutes   27017/tcp                mongodb
```

### 4. 같은 네트워크 사용 시 장점

* 같은 네트워크를 사용하면 아래와 같이 다른 컨테이너를 이름으로 호출할 수 있다.

```jsx
mongoose.connect(
  'mongodb://mongodb:27017/swfavorites',
  { useNewUrlParser: true },
  (err) => {
    if (err) {
      console.log(err);
    } else {
      app.listen(3000);
    }
  }
);
```

```
$ docker ps -a
CONTAINER ID   IMAGE         COMMAND                  CREATED         STATUS         PORTS                    NAMES
872564e10e28   network-app   "docker-entrypoint.s…"   3 seconds ago   Up 2 seconds   0.0.0.0:3000->3000/tcp   network-app
ccd4c8b04d74   mongo         "docker-entrypoint.s…"   5 minutes ago   Up 5 minutes   27017/tcp                mongodb
```