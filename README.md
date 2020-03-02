# Docker cheat sheet
https://docs.docker.com/engine/reference/commandline/docker/

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

### Build image from dockerfile
`docker build -t <your username>/node-web-app .` <br>
this generates an image

### Create running container from docker image
`docker run -p 49160:8080 -d <your username>/node-web-app` <br>
The `p` argument is the port, it maps from host port to docker port.

## Basic commands

`docker images` - list non intermediate images <br>
`docker ps` -  list all running containers <br>
`docker ps -a` -  list all containers <br>
`docker system prune` - removes non running and dangling imaged "images that are tagged and not referenced by any container."<br>

## Concepts

**Image** - Built container, no state. <br>
**Container** - running instance of an **Image**

## Resources

Filesystem perf for mac - https://docs.docker.com/docker-for-mac/osxfs-caching/