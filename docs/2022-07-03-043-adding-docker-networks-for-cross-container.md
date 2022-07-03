## Adding Docker Networks for Efficient Cross-Container

### 1. Making Network

```
$ docker network create goals-net    
6d41261f8bdf5d5d742a09a0bf68f3c7c4af1599cfd12e277de189a47eeaa3f8

$ docker network ls              
NETWORK ID     NAME            DRIVER    SCOPE
41738f182287   bridge          bridge    local
2879ee64486f   favorites-net   bridge    local
6d41261f8bdf   goals-net       bridge    local
969819b69df5   host            host      local
2e7d396ba961   none            null      local
```

### 2. Connect MongoDB with network

```
$ docker run\
    --name mongodb\
    --rm\
    -d\
    --network goals-net\
    mongo
b2cf1f8c69901e9355473d77fcd47c4c102d145130e1cfd4ea21e3b173ccab22

$ docker ps -a
CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS         PORTS       NAMES
b2cf1f8c6990   mongo     "docker-entrypoint.s…"   2 seconds ago   Up 2 seconds   27017/tcp   mongodb
```

### 3. Connect Backend Service with network

```
$ docker run\
    --name goals-backend\
    --rm\
    -d\
    --network goals-net\
    goals-node

$ docker ps -a
CONTAINER ID   IMAGE        COMMAND                  CREATED         STATUS         PORTS       NAMES
87a44341aae6   goals-node   "docker-entrypoint.s…"   4 seconds ago   Up 4 seconds   80/tcp      goals-backend
b2cf1f8c6990   mongo        "docker-entrypoint.s…"   7 minutes ago   Up 7 minutes   27017/tcp   mongodb
```

### 4. Connect Frontend Service with network

```
$ docker run\
    --name goals-frontend\
    --rm\
    -d\
    -it\
    --network goals-net\
    -p 3000:3000\
    goals-react

$ docker ps -a
CONTAINER ID   IMAGE         COMMAND                  CREATED          STATUS          PORTS                    NAMES
8052a9f8e0d9   goals-react   "docker-entrypoint.s…"   4 seconds ago    Up 3 seconds    0.0.0.0:3000->3000/tcp   goals-frontend
87a44341aae6   goals-node    "docker-entrypoint.s…"   3 minutes ago    Up 3 minutes    80/tcp                   goals-backend
b2cf1f8c6990
```