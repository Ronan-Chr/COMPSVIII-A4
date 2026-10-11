# Assignment #4: Application Containerization

This is a simple Node.js web application designed for learning Docker containerization concepts.

## Application Overview

This application is a basic Express.js web server that:
- Serves a static HTML page at the root (`/`)
- Provides an API status endpoint at `/api/status`
- Includes a health check endpoint at `/health`
- Runs on port 3000 by default (configurable via PORT environment variable)

## What's Included

- **app.js**: Main application server file
- **package.json**: Node.js dependencies and project configuration
- **public/index.html**: Static HTML page that confirms successful containerization
- **public/style.css**: Styling for the web page

## Running Without Docker (for reference only)

If you wanted to run this application directly (not required for assignment):
```bash
npm install
npm start
```

## Your Docker Assignment

**DO NOT MODIFY THE APPLICATION CODE**

Your task is to containerize this existing application using Docker. You need to:

1. Create a `Dockerfile` that properly containerizes this Node.js application
2. Build a Docker image from your Dockerfile
3. Run a container from your image
4. Verify the application works by accessing it in your browser

## Starting the Application

- To build the docker image run the command:

```bash
docker build -t compsviii-a4 . 
```

- To run your docker container in port 3000 run the command:

```bash
docker run -d -p 3000:3000 --name compsviii-a4-container compsviii-a4
```

## Screenshots

- Docker Build Command working 

![The Terminal after success](Screenshots\Docker.Build.png)

- This shows the status when at http://localhost:3000/api/status for the api

![API Status](Screenshots\API.Results.png)

- This is the Docker Container working and what the index.html shows once it is.

![Docker Index](Screenshots\Index.HTML.png)

## Reflection Question
**Answer the following question in the space below**: How does containerization with Docker differ from using virtual machines, and why might a development team choose Docker containers over VMs for deploying applications like the one you just containerized?

- The big difference between a VM and a Docker Container is that a VM runs an entirely different OS or a copy of once on your computer to have two seperate enviornments (Can affect system files in one and not the other). Docker uses parts of your computer and only finds whats needed inside the container for the program to work correctly and it packages it into the container. Dockers are much more forgiving in terms of hardware when looking at what they can be pushed to do because it requires less from the parts.

- A development team might opt for containers over VMs because of money or resources of a company using Docker could require significantly less hardware server side to actually get a server to run it on where with Docker the file can have set instructions to not bottleneck parts when using the container. The other thing is the setup with a VM is much more complicated having to move things into the VMs enviornment needed for a program to run vs typing the build command for the dockerfile container can save hours for a dev team.

## Application Requirements for Docker

Your Dockerfile should ensure:
- The application has Node.js runtime available
- All application files are copied into the container
- Dependencies are installed (`npm install`)
- Port 3000 is exposed
- The application starts with `npm start`
- The container can be accessed from your host machine

## Verification

When your Docker container is running correctly:
- Navigate to `http://localhost:3000` (or whatever port you mapped)
- You should see a success page confirming containerization worked
- The `/api/status` endpoint should return JSON status information

## Troubleshooting Tips

- Make sure your port mapping is correct in the `docker run` command
- Check that all files are copied into the container
- Verify Node.js dependencies are installed in the container
- Use `docker logs <container-name>` to see application output

## File Structure Expected
```
docker-assignment/
├── Dockerfile          # You create this
├── app.js              # Provided
├── package.json        # Provided
├── public/             # Provided
│   ├── index.html      # Provided
│   └── style.css       # Provided
└── README.md           # This file
```

Good luck with your Docker containerization!