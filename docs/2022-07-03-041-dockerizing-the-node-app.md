## Dockerizing the Node App

### 1. Node Dockerfile

```dockerfile
FROM node:14

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

EXPOSE 80

CMD ["node", "app.js"]
```

### 2. Run Docker container

```
$ docker build -t goals-node .

$ docker run\
    --name goals-backend\
    --rm\
    -d\
    -p 80:80\
    goals-node
```