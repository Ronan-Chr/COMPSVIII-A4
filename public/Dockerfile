# Uses node 16 as the base image for the container which includes the Node.js runtime and npm
FROM node:16

# Sets the working directory for the program inside the container to the /app folder for the following lines
WORKDIR /app

# Copy the packages from json to allow for caching during installation
COPY package*.json ./

# Installs the application dependencies in the container before launch
RUN npm install

# Copies the rest of the application source code into the container
COPY . .

# Exposes port 3000 for the application in the container by listening on port 3000
EXPOSE 3000

# Starts on launch when running program from command terminal
CMD ["npm", "start"]