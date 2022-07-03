## Dockerizing the mongoDB service

### 1. MongoDB 컨테이너 올리기

```
$ docker run\
    --name mongodb\
    --rm\
    -d\
    --network goals-net\
    mongo
```