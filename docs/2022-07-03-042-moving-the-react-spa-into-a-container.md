## Moving the react SPA into a container

### 1. Dockerfile

```dockerfile
FROM node:14 as builder

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

EXPOSE 3000

CMD ["npm", "start"]
```

### 2. Run Docker Container

```
$ docker build -t goals-react .
[+] Building 49.8s (11/11) FINISHED
 => [internal] load build definition from Dockerfile                                                               0.0s
 => => transferring dockerfile: 162B                                                                               0.0s
 => [internal] load .dockerignore                                                                                  0.0s
 => => transferring context: 2B                                                                                    0.0s
 => [internal] load metadata for docker.io/library/node:14                                                         2.4s
 => [auth] library/node:pull token for registry-1.docker.io                                                        0.0s
 => [internal] load build context                                                                                  0.0s
 => => transferring context: 1.18MB                                                                                0.0s
 => [1/5] FROM docker.io/library/node:14@sha256:ce156f9b2e9dbe73139cf0619a71188960e6c9eaba0ff832a5dfa0febf9eee27   0.0s
 => CACHED [2/5] WORKDIR /app                                                                                      0.0s
 => [3/5] COPY package.json .                                                                                      0.0s
 => [4/5] RUN npm install                                                                                         41.8s
 => [5/5] COPY . .                                                                                                 0.0s
 => exporting to image                                                                                             5.4s
 => => exporting layers                                                                                            5.4s
 => => writing image sha256:f280c934f7c9b6d191bba9040662eb0054bfbf2ff036d22a2f7dd07bdcadf485                       0.0s
 => => naming to docker.io/library/goals-react               

$ docker run\
    --name goals-frontend\
    --rm\
    -d\
    -it\
    -p 3000:3000\
    goals-react
```