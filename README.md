# Strapi-Dockerization-Task

# Strapi Application Dockerization (Local Setup)
## Task Objective

The objective of this task was to **containerize a Strapi application using Docker and run it locally**. This included creating a Dockerfile, building a Docker image, running the container, resolving real-time errors, and successfully accessing the Strapi Admin UI.

## System Prerequisites (Verified)

Before starting the task, the following tools were verified on the local system:

* Node.js installed (v24.x on local machine)
* Docker Desktop installed and running
* Docker CLI available
* Windows OS

---

## Step-by-Step Work Done

### Step 1: Create Project Directory

A fresh directory was created for the task:

```
C:\Users\DELL\strapi-docker-app
```

This directory contains the Strapi project and Dockerfile.

---

### Step 2: Create Dockerfile

A Dockerfile was created inside the project directory to containerize the Strapi application.

Key actions performed in Dockerfile:

* Used official Node.js base image
* Set working directory inside container
* Copied `package.json` and `package-lock.json`
* Installed dependencies using `npm install`
* Copied entire project source code
* Exposed Strapi default port (1337)
* Started Strapi application

---

### Step 3: Build Docker Image

The Docker image was built using the following command:

```
docker build -t strapi-app .
```

During the build process:

* Faced Node version compatibility issues
* Observed Strapi v5 requires Node >=20
* Adjusted base image accordingly

---

### Step 4: Handle Build Errors

During `npm install` and `npm run build`, the following issues were encountered and resolved:

#### Node Version Mismatch

* Error due to Node 18 inside Docker
* Fixed by using Node 20+ base image

#### better-sqlite3 Build Failure

* Required native compilation tools
* Python dependency identified during troubleshooting

#### TypeScript Errors in admin.ts

* Errors related to incorrect usage of `env`
* Understood Strapi v5 configuration expectations

#### Missing Admin JWT Secret

* Error: `Missing admin.auth.secret configuration`
* Learned importance of environment variables in Strapi v5

---

### Step 5: Run Docker Container

The Strapi container was started using:

```
docker run -d -p 1337:1337 --name strapi-container strapi-app
```

Port mapping:

* Host: 1337
* Container: 1337

---

### Step 6: Verify Container Status

Checked running containers:

```
docker ps
```

Confirmed container was running successfully.

---

### Step 7: Access Strapi Application

Accessed Strapi Admin UI in browser:

```
http://localhost:1337/admin
```

Successfully reached:

* Strapi Admin Panel
* Admin user creation page

---

## Docker Commands Used

* Build image:

```
docker build -t strapi-app .
```

* Run container:

```
docker run -d -p 1337:1337 --name strapi-container strapi-app
```

* List containers:

```
docker ps
```

* View logs:

```
docker logs strapi-container
```

* Stop container:

```
docker stop strapi-container
```

* Remove container:

```
docker rm -f strapi-container
```

---

## Key Learnings

* Understood Strapi v5 Node.js requirements
* Learned Dockerfile structure for Node.js applications
* Gained hands-on experience troubleshooting Docker build errors
* Learned importance of environment variables in Strapi
* Successfully ran Strapi inside Docker locally

---

## Final Status

-> Strapi application successfully containerized
-> Docker image built successfully
-> Container running locally
-> Admin UI accessible on browser

---

## Conclusion

This task provided real-world DevOps experience by combining **Docker, Node.js, and Strapi**. It involved debugging multiple issues and understanding how application dependencies behave inside containers.


