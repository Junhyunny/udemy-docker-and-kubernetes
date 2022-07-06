## A First Deployment - Using the Imperative Approach

### 1. image build

```
$ docker build -t kub-first-app .
```

### 2. deployment 만들기

* 첫번째 명령의 실행 결과 로그는 성공한 것처럼 보이지만, 실제로 배포는 실패한 것이다.
* 도커 허브에 이미지를 올리면 된다.

```
$ kubectl create deployment first-app --image=kub-first-app
deployment.apps/first-app created

$ docker build -t opop3966/kub-first-app .
[+] Building 2.6s (10/10) FINISHED                                                                                    
 => [internal] load build definition from Dockerfile                                                             0.0s
 => => transferring dockerfile: 36B                                                                              0.0s
 => [internal] load .dockerignore                                                                                0.0s
 => => transferring context: 34B                                                                                 0.0s
 => [internal] load metadata for docker.io/library/node:14-alpine                                                2.5s
 => [1/5] FROM docker.io/library/node:14-alpine@sha256:6b87d16e4ce20cacd6f1f662f66c821e4c3c41c2903daeace52d818e  0.0s
 => [internal] load build context                                                                                0.0s
 => => transferring context: 92B                                                                                 0.0s
 => CACHED [2/5] WORKDIR /app                                                                                    0.0s
 => CACHED [3/5] COPY package.json .                                                                             0.0s
 => CACHED [4/5] RUN npm install                                                                                 0.0s
 => CACHED [5/5] COPY . .                                                                                        0.0s
 => exporting to image                                                                                           0.0s
 => => exporting layers                                                                                          0.0s
 => => writing image sha256:d212347e667475a6cdad1203e0b27f9fc0f29c739ff56a4717182c5a585a3789                     0.0s
 => => naming to docker.io/opop3966/kub-first-app

$ docker push opop3966/kub-first-app:latest
The push refers to repository [docker.io/opop3966/kub-first-app]
92632d341e2f: Pushed 
c75d365fe6eb: Pushed 
885f6756cc78: Pushed 
feec79471c5d: Mounted from opop3966/hello-world 
d0baefd97422: Mounted from opop3966/hello-world 
92c140f8363b: Mounted from opop3966/hello-world 
cc7cd04ea96f: Mounted from opop3966/hello-world 
24302eb7d908: Mounted from opop3966/hello-world 
latest: digest: sha256:dca5fbf456441258f31337621b231a7bb8f070fb1a9f241519cf135dbd3af395 size: 1990

$ kubectl create deployment first-app --image=opop3966/kub-first-app:latest
deployment.apps/first-app created

$ kubectl get deployments
NAME        READY   UP-TO-DATE   AVAILABLE   AGE
first-app   1/1     1            1           13s

$ kubectl get pods       
NAME                         READY   STATUS    RESTARTS   AGE
first-app-6c9d7ff88b-frh78   1/1     Running   0          39s
```

### 3. deployment 확인하기

* 실제 동작하고 있는 deployments object는 존재하지 않는다.

```
$ kubectl get deployments
NAME        READY   UP-TO-DATE   AVAILABLE   AGE
first-app   0/1     1            0           49s
```

### 4. pods 확인하기

* 실제로 만들어지지 않았다.

```
$ kubectl get pods
NAME                        READY   STATUS             RESTARTS   AGE
first-app-fbcb6c876-f84wj   0/1     ImagePullBackOff   0          82s
```

### 5. deployments 삭제하기

```
$ kubectl delete deployment first-app
deployment.apps "first-app" deleted

$ kubectl get deployments
No resources found in default namespace.
```