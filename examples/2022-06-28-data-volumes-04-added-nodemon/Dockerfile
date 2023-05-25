FROM node:14

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

EXPOSE 80

# VOLUME [ "/app/node_modules" ]

# VOLUME [ "/app/temp" ]

CMD [ "npm", "start" ]