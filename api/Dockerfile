# This is adding a parent image. Use 'FROM' keyword for it
# Pull the node image into our image as our initial layer, in the beginning/ 16 version of Node, Alpine Distribution of Linux
FROM node:16-alpine 

#nodemon for watching the changes in the file to restart the server
RUN npm install -g nodemon

# We are mentioning Working directory here so that every instruction after that can use the Working Directory,
WORKDIR /app

#Copying the package.json file before so that we can install teh dependecies first.
COPY package.json .

#Specifying the command that we want ot run while the image is being build. RUN <command>.
#Here we are installing all the node dependencies that are required.
# But simply writing this won't work because we have loaded our files in /app folder (See COPY . /app) and RUN npm install works on the root folder.
# Thus, we need to add working directory: WORKDIR (See Above)
RUN npm install

#This is to load our files into the docker: COPY <source> <destination>, if our files were on src folder of the root folder then the source would be /src, '.' indicates the root folder
# COPY . /app After adding the working directory this won't work because the instruction will turn into COPY . /app/app because the WORKDIR is /app and we don't want that so.
COPY . .

# We need to expose the port because this app will be running in the container and not our computer. So we need to specify which port of the container to expose for the app to run.
# * The Port in app.js is also 4000
# This is optional. Only required when we're running the app on Docker Desktop for port mapping. [I have no idea what that is]
# This won't be needed if you run the docker from command line but it's good to have it.
EXPOSE 4000

# We won't be using RUN node app.js like we would normally run a node application because it won't work as RUN instruction would RUN the instruction while the image is being created so it won't work as we don't have the application to run.
# Image are just blueprint of the application that we want to run so it makes sense to run the npm install command in the build time but not node app.js since we're not running the image we're just building the image.
# So, instead we use the command CMD like below to run the command only when we have a running instance of the image.
CMD [ "npm","run","dev" ]



