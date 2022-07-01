
## Using and Running External Images

### 1. 이미지를 사용하는 방법

1. 이미 만들어진 이미지를 사용한다.
    * 동료가 미리 만든 이미지를 사용한다.
    * 커뮤니티에서 만든 이미지를 사용한다.
    * 도커 허브에 미리 만들어져서 올라가 있는 이미지를 사용한다.
1. 이미지를 만들어서 사용한다.
    * /projects/2022-06-25-nodejs-app-starting-setup 참조
    * Dockerfile 작성(based on another image)

##### Dockerfile 예시

```dockerfile
# base image
FROM node

# move working directory inside of my image 
WORKDIR /app

# copy source, resources into my image
# COPY .(from, current directory local) ./(to, '/app' directory inside of my image)
COPY . ./

# run command inside of my image 
RUN npm install

# let docker know what port is container uses
EXPOSE 80

# start node server based on my image
CMD ["node", "server.js"]
```