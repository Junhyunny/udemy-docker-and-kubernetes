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