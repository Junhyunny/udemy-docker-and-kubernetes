## Live Source Code Update for the React Container(with Bind Mounts)

### 1. Bind Mount를 통한 소스 코드 디렉토리 연결

```
$ docker run\
    --name goals-frontend\
    --rm\
    --network goals-net\
    -p 3000:3000\
    -d\
    -it\
    -v "/Users/junhyunk/Desktop/workspace/udemy/udemy-docker-and-kubernetes/projects/2022-07-03-multi-01-starting-setup/frontend/src":/app/src\
    goals-react
```