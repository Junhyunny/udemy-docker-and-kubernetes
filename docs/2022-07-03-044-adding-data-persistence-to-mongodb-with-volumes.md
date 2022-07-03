## Adding Data Persistence to MonogoDB with Volumes

### 1. Volume 명령어 추가

* MongoDB docker image documentation에서 확인 가능

```
$ docker run\
    --name mongodb\
    --rm\
    -d\
    --network goals-net\
    -v mongo-data:/data/db\
    mongo
```

### 2. MongoDB Security

* MongoDB docker image documentation에서 확인 가능

```
$ docker run\
    --name mongodb\
    --rm\
    -d\
    --network goals-net\
    -v mongo-data:/data/db\
    -e MONGO_INITDB_ROOT_USERNAME=mongoadmin\
    -e MONGO_INITDB_ROOT_PASSWORD=secret\
    mongo
```