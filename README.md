# Docker cheat sheet

## Basic Dockerfile for nodejs

```Dockerfile
FROM node:10

# Create app directory
WORKDIR /usr/src/app

# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
# where available (npm@5+)
COPY package*.json ./

RUN npm install
# If you are building your code for production
# RUN npm ci --only=production

# Bundle app source
COPY . .

EXPOSE 8080
CMD [ "node", "server.js" ]
```

### Build dockerfile
`docker build -t <your username>/node-web-app .`

### Run built docker image
`docker run -p 49160:8080 -d <your username>/node-web-app` <br>
The `p` argument is the port, it maps from host port to docker port.

## Basic commands

`docker ps` -  list all running containers <br>
`docker ps -a` -  list all containers <br>
`docker system prune` - removes non running and dangling imaged "is one that is not tagged and is not referenced by any container."<br>
`docker images` - show built non intermediate images
