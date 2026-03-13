


INTERVIEW Questions

**2. What is a Container?**
A container is a lightweight, standalone executable package that includes:

  Application code
  
  Runtime
  
  Libraries
  
  Dependencies
  
Containers run on the host OS kernel, making them faster than virtual machines.

**3. Difference between Docker and Virtual Machine**

      Feature          	Docker	      Virtual Machine
      Virtualization	  OS-level	      Hardware-level
      Boot time	        Seconds        	Minutes
      Size	            MBs	            GBs
      Performance	      Faster	        Slower

**4. What is a Docker Image?**
      A Docker Image is a read-only template used to create containers.
      
      Example:
      
      docker pull nginx

4. What is a Docker Image?
A Docker Image is a read-only template used to create containers.

Example:

docker pull nginx

5. What is a Docker Container?
A running instance of a Docker image.

Example:

docker run nginx
2. Intermediate Docker Questions

6. What is Dockerfile?
A text file containing instructions to build a Docker image.

Example:

FROM node:18
WORKDIR /app
COPY . .
RUN npm install
CMD ["node","app.js"]

7. What are the main components of Docker?

Docker Engine

Docker Client

Docker Daemon

Docker Images

Docker Containers

Docker Registry

8. What is Docker Hub?
A cloud registry where Docker images are stored and shared.

Example:

docker pull ubuntu

9. What is Docker Compose?
Docker Compose is used to run multiple containers using a single YAML file.

Example:

version: "3"
services:
  web:
    image: nginx
    ports:
      - "80:80"

Run:

docker-compose up

10. What is the difference between CMD and ENTRYPOINT?

CMD	ENTRYPOINT
Default command	Fixed command
Can be overridden	Hard to override

Example:

CMD ["node","app.js"]
3. Advanced Docker Interview Questions

11. What are Docker volumes?
Volumes are used for persistent storage so data is not lost when containers stop.

Example:

docker volume create mydata

12. What is Docker networking?

Types of Docker networks:

Bridge (default)

Host

None

Overlay

Macvlan

Example:

docker network create mynetwork

13. What is multi-stage build?
Used to reduce Docker image size.

Example:

FROM node:18 as build
WORKDIR /app
COPY . .
RUN npm install

FROM node:18-alpine
COPY --from=build /app /app
CMD ["node","app.js"]

14. Difference between COPY and ADD

COPY	ADD
Simple file copy	Can download URLs
Preferred	Less predictable

15. What is Docker Swarm?
Docker Swarm is Docker's native container orchestration tool used to manage multiple containers across nodes.

4. Practical Docker Commands (Interview Favorite)

Check running containers

docker ps

Build image

docker build -t myapp .

Run container

docker run -p 8080:80 nginx

Stop container

docker stop container_id

Remove container

docker rm container_id
5. Scenario-Based Questions

1. How do you reduce Docker image size?

Use Alpine images

Use multi-stage builds

Remove unnecessary dependencies

2. How do you debug a running container?

docker exec -it container_id /bin/bash

3. How do you scale containers?
Using Docker Compose

docker-compose up --scale web=3

or Kubernetes
