init git -y
add run tests on package.json

init .github/workflows/pipeline.yaml

> hello-docker
  > dockerfile
  > hello.js
  
in dockerfile :
FROM node:20-alpine
WORKDIR /app
COPY . .
CMD node hello.js

// get the version from official iamges > node

$ docker build -t hello-docker .
$ docker images
$ docker run hello-docker

// dock_desktop > container > currentone > inside that you'll find the lod detials form the hello.js

$ docker run -it hello-docker sh
$ node hello.js 

$npm create vite@latest react-docker
 > react
 > typescript

+ Dockerfile > into react-docker
+ .dockerignore

$ cd to react docker 
$ docker build -t react-docker .
$ docker run react-docker
// link wont show anything on port 5173

$ docker run -p 5173:5173 react-docker
// same issue will occur 
package.json > "dev" :"Vite --host"

//Kill termincal and rerun
//error will occur > cuz u have accumulated a lot of images
$ docker ps
$ docker ps -a // lists all the container
$ docker stop (starting 3 digits) or entire name
// in desktop that container is no longer rrunning

$ docker container prune // wil remove all inactive containers
$ docker remove aa5() --force

> docker build -t react-docker .
> docker run -p 5173:5173 react-docker //works this timee but any changes updated wont be reflected into the local host
> docker run -p 5173:5173 -v "$(pwd):/app" -v /app/node_modules react-docker 
// local code is linked to the container and any changes made will be reflected in the running container
-v = volume

@ btw in vite change the config file : events 
> docker run -p 5173:5173 -v "a:/lil projects/devOps/react-docker:/app" -v /app/node_modules react-docker 
 -----------------------------
 # Development: Run locally
npm run dev

# When ready to test in Docker:
docker build -t react-docker .
docker run -p 5173:5173 react-docker
-------------------------------------
//////////this one worksss///////////
+ docker-compose.yml
version: '3.8'

services:
  react-app:
    build: .
    ports:
      - "5173:5173"
    volumes:
      - .:/app
      - /app/node_modules
    environment:
      - CHOKIDAR_USEPOLLING=true
      - CHOKIDAR_INTERVAL=100
    stdin_open: true
    tty: true

> docker-compose up
-------------------------------
> docker login
> docker tag react-docker akii7/react-docker 
//successfully published into the cloud
