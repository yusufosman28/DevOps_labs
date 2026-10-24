# Docker

![Containers](https://img.shields.io/badge/Containers-Docker-2496ED?logo=docker&logoColor=white)
![Compose](https://img.shields.io/badge/Docker-Compose-2496ED?logo=docker&logoColor=white)
![Focus](https://img.shields.io/badge/Focus-Containerisation-purple)
![Practice](https://img.shields.io/badge/Practice-Hands--on-orange)

This folder documents my hands-on learning of **Docker**, from writing my own Dockerfile to running a Flask app and MySQL together with Docker Compose and publishing an image to Docker Hub, followed by the problems I hit and how I fixed them.

Containers package an application with everything it needs, so it runs the same on a laptop, in a CI pipeline and in production. Docker is the foundation for container platforms such as Amazon ECS and Kubernetes.

My focus has been on **understanding how images, containers and networks behave**, and on reading build output and logs to find the real cause of a problem.

The code for the projects in these notes is in my [docker-learning](https://github.com/yusufosman28/docker-learning) repository, and my published image is on [Docker Hub](https://hub.docker.com/r/yusufosman1280/flask-mysql).

---

## Learning Objectives

Through this module, I aimed to:

- Explain what containers are and how they differ from virtual machines
- Write Dockerfiles and understand how image layers and caching work
- Build, run, inspect and stop containers
- Connect containers using Docker networks
- Read container logs and exit codes to diagnose problems
- Run a multi-container application with Docker Compose
- Push images to a registry and pull them back

---

## Topics Covered

### Fundamentals

- [Containers and Docker](./fundamentals/01-containers-and-docker.md)  
  What a container is, Docker's main parts, and why containers matter.

- [VMs vs Containers](./fundamentals/02-vms-vs-containers.md)  
  How containers share the host kernel and when a VM is still the right choice.

- [Dockerfiles and Images](./fundamentals/03-dockerfiles-and-images.md)  
  Dockerfile instructions, layers, caching and slim base images.

- [Building and Running Containers](./fundamentals/04-building-and-running.md)  
  `docker build`, `docker run`, port publishing and managing containers.

- [Docker Networking](./fundamentals/05-docker-networking.md)  
  Bridge, host and none networks, and finding containers by name.

- [Multi-Container Applications](./fundamentals/06-multi-container-apps.md)  
  Connecting a Flask container to a MySQL container.

- [Logs and Exit Codes](./fundamentals/07-logs-and-exit-codes.md)  
  Reading `docker logs`, stopping containers and understanding exit codes.

- [Docker Compose](./fundamentals/08-docker-compose.md)  
  Defining and running a multi-container application from one file.

- [Registries and Docker Hub](./fundamentals/09-registries-and-docker-hub.md)  
  Tagging, pushing and pulling images.

---

### Troubleshooting

- [What Broke and How I Fixed It](./troubleshooting)  
  Real build and runtime errors from my own projects, broken down into problem, cause, fix and lesson.

---

## Learning Approach

- Every topic practised hands-on on Ubuntu (WSL 2) with Docker Desktop
- My own Dockerfiles and compose file, adapted from the course to my own setup rather than copied
- Errors diagnosed from build output and container logs before looking up answers
- Results measured where possible, such as comparing image sizes

---

## Folder Structure

```
05-docker/
├── README.md
├── fundamentals/
│   ├── README.md
│   ├── 01-containers-and-docker.md
│   ├── 02-vms-vs-containers.md
│   ├── 03-dockerfiles-and-images.md
│   ├── 04-building-and-running.md
│   ├── 05-docker-networking.md
│   ├── 06-multi-container-apps.md
│   ├── 07-logs-and-exit-codes.md
│   ├── 08-docker-compose.md
│   └── 09-registries-and-docker-hub.md
└── troubleshooting/
    ├── README.md
    ├── 01-mysqlclient-build-failed.md
    ├── 02-pull-access-denied.md
    ├── 03-compose-file-in-the-wrong-folder.md
    ├── 04-size-test-gave-identical-results.md
    └── 05-missing-dots-in-build-commands.md
```
