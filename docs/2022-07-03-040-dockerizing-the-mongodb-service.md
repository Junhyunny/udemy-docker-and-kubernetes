## Dockerizing the mongoDB service

### 1. MongoDB 컨테이너 올리기

* 기본적인 MongoDB 서비스를 올립니다.

```
$ docker run\
    --name mongodb\
    --rm\
    -d\
    -p 27017:27017\
    mongo
```