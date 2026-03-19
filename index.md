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
