## Updating Deplyoments

### 1. Docker Image Rebuild and Push

```
$ docker build -t opop3966/kub-first-app . 
[+] Building 2.9s (11/11) FINISHED                                                                                    
 => [internal] load build definition from Dockerfile                                                             0.0s
 => => transferring dockerfile: 36B                                                                              0.0s
 => [internal] load .dockerignore                                                                                0.0s
 => => transferring context: 34B                                                                                 0.0s
 => [internal] load metadata for docker.io/library/node:14-alpine                                                2.8s
 => [auth] library/node:pull token for registry-1.docker.io                                                      0.0s
 => [1/5] FROM docker.io/library/node:14-alpine@sha256:6b87d16e4ce20cacd6f1f662f66c821e4c3c41c2903daeace52d818e  0.0s
 => [internal] load build context                                                                                0.0s
 => => transferring context: 422B                                                                                0.0s
 => CACHED [2/5] WORKDIR /app                                                                                    0.0s
 => CACHED [3/5] COPY package.json .                                                                             0.0s
 => CACHED [4/5] RUN npm install                                                                                 0.0s
 => [5/5] COPY . .                                                                                               0.0s
 => exporting to image                                                                                           0.0s
 => => exporting layers                                                                                          0.0s
 => => writing image sha256:357ee2d3a2f42acd0025902dd8db59d6153384c687a245e486e380906911b52c                     0.0s
 => => naming to docker.io/opop3966/kub-first-app                                                                

$ docker push opop3966/kub-first-app:latest
The push refers to repository [docker.io/opop3966/kub-first-app]
db72aec2aa9f: Pushed 
c75d365fe6eb: Layer already exists 
885f6756cc78: Layer already exists 
feec79471c5d: Layer already exists 
d0baefd97422: Layer already exists 
92c140f8363b: Layer already exists 
cc7cd04ea96f: Layer already exists 
24302eb7d908: Layer already exists 
latest: digest: sha256:5fbf63b4cf5d4c8736dd3b71ee368fcdc823236400d7426f9e0f3def4e7da150 size: 1990
```

### 2. Set new image at deployment

* 새로운 이미지를 지정해주더라도 변경이 없다.
* 태그의 변경이 없었기 때문에 이미지를 새로 다운받기만하고 Pod 재배포를 수행하지 않는다.

```
$ kubectl set image deployment/first-app kub-first-app=opop3966/kub-first-app
deployment.apps/first-app image updated
```

* 새로운 태그로 이미지를 만들어 deployment를 변경한다.
* `kubectl rollout` 명령어를 통해 deployment의 상태를 확인한다.

```
$ docker build -t opop3966/kub-first-app:0.1 .
[+] Building 2.5s (11/11) FINISHED
 => [internal] load build definition from Dockerfile                                                                     0.0s
 => => transferring dockerfile: 36B                                                                                      0.0s
 => [internal] load .dockerignore                                                                                        0.0s
 => => transferring context: 34B                                                                                         0.0s
 => [internal] load metadata for docker.io/library/node:14-alpine                                                        2.4s
 => [auth] library/node:pull token for registry-1.docker.io                                                              0.0s
 => [internal] load build context                                                                                        0.0s
 => => transferring context: 92B                                                                                         0.0s
 => [1/5] FROM docker.io/library/node:14-alpine@sha256:6b87d16e4ce20cacd6f1f662f66c821e4c3c41c2903daeace52d818ec3f4bbdd  0.0s
 => CACHED [2/5] WORKDIR /app                                                                                            0.0s
 => CACHED [3/5] COPY package.json .                                                                                     0.0s
 => CACHED [4/5] RUN npm install                                                                                         0.0s
 => CACHED [5/5] COPY . .                                                                                                0.0s
 => exporting to image                                                                                                   0.0s
 => => exporting layers                                                                                                  0.0s
 => => writing image sha256:357ee2d3a2f42acd0025902dd8db59d6153384c687a245e486e380906911b52c                             0.0s
 => => naming to docker.io/opop3966/kub-first-app:0.1                                                                    0.0s

$ docker push opop3966/kub-first-app:0.1   
The push refers to repository [docker.io/opop3966/kub-first-app]
db72aec2aa9f: Layer already exists 
c75d365fe6eb: Layer already exists 
885f6756cc78: Layer already exists 
feec79471c5d: Layer already exists 
d0baefd97422: Layer already exists 
92c140f8363b: Layer already exists 
cc7cd04ea96f: Layer already exists 
24302eb7d908: Layer already exists 
0.1: digest: sha256:5fbf63b4cf5d4c8736dd3b71ee368fcdc823236400d7426f9e0f3def4e7da150 size: 1990

$ kubectl set image deployment/first-app kub-first-app=opop3966/kub-first-app:0.1
deployment.apps/first-app image updated

$ kubectl rollout status deployment/first-app
deployment "first-app" successfully rolled out
```