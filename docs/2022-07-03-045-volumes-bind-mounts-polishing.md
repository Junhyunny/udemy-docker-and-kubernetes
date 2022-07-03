## Volumes, Bind Mounts and Polishing for the NodeJS Container

### 1. Volumes, Bind Mounts, Polishing for the backend service

```
$ docker run\
    --name goals-backend\
    --rm\
    --network goals-net\
    -v "/Users/junhyunk/Desktop/workspace/udemy/udemy-docker-and-kubernetes/projects/2022-07-03-multi-01-starting-setup/backend":/app\
    -v logs:/app/logs\
    -v /app/node_modules\
    -d\
    goals-node
```

### 2. Using USER_NAME, PASSWORD using Dockerfile

```
$ docker run\
    --name goals-backend\
    --rm\
    --network goals-net\
    -v "/Users/junhyunk/Desktop/workspace/udemy/udemy-docker-and-kubernetes/projects/2022-07-03-multi-01-starting-setup/backend":/app\
    -v logs:/app/logs\
    -v /app/node_modules\
    -e MONGODB_USERNAME=mongoadmin\
    -e MONGODB_PASSWORD=secret\
    -d\
    goals-node
```