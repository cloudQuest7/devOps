# set the base image to create the images for react app
FROM node:20-alpine


#create a user with permissions to run the app
# -S -> create a system user
# -G -> add the user to a group
# this is done to avoid running the app as root, which is a security risk
# If the app is run as a root, any vulnerability in the app can be exploited to gain access to the host machine
# Its a good practice to run the app as a non-root user, especially in production environments
RUN addgroup app && adduser -S app -G app

# set the user to run the app
USER app

# set the working directory in the container
WORKDIR /app

#copy pckage.json and package-lock.json to the working directory
# this is fone before copying the rest of the files to take advantage of Docker's caching mechanism
# If the package.json files haven't changed, Docker will use the cached layer for npm install, which can speed up the build process
COPY package*.json ./

# Sometimes the ownership of the files in the working dir is changes to root
# and thus the app user doesn't have permission to access them, so we need to change the ownership of the files to the app user and then throws and error -> "EACCES: permission denied, open 'package-lock.json'"
# to avoid this, change the ownership of the files to the app user before running npm install
USER root

# change the ownership of the files to the app user
# chown -R -> change the ownership of the files recursively
# chown changes the ownership of the files to the app user and group
RUN chown -R app:app .

USER app

RUN npm install

# copy the rest of the files to the working directory
COPY . .

# expose the port that the app will run on
EXPOSE 5173

# set the command to run the app
CMD npm run dev