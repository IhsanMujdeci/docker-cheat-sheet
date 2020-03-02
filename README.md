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
this generates an image with the `-t` tag supplied

### Create running container from docker image
`docker run -p 49160:8080 -d <your username>/node-web-app` <br>
The `-p` argument is the port, it maps from host port to docker port.<br>
The `-d` argument stands for detached, runs the container in the background

## Basic commands

`docker images` - list non intermediate images 

`docker ps` (Process Status) -  list all running containers
- `-a ` list all containers 

`docker system prune` - removes non running and dangling images (which are images that are tagged and not referenced by any container).<br>

## Concepts

**Image** - Built container, no state. <br>
**Container** - running instance of an **Image**

## Resources

Filesystem perf for mac - https://docs.docker.com/docker-for-mac/osxfs-caching/