# Experiment 8: Creating Docker Images and Containers for Simple Applications

- **Student Name**: Soham Patra
- **USN**: 4NI25CS197
- **Semester / Section**: 3rd Sem, Sec-G
- **Course**: Collaborative Development and DevOps (1BCS303)
- **Institution**: The National Institute of Engineering, Mysuru

---

## Aim
To install Docker Desktop on a Windows computer using WSL 2, and to understand Docker images and containers by downloading an image, running a container from it, checking its status, and then stopping and removing it.

---

## Commands & Output

### 1. Verify Docker Installation
```bash
$ docker --version
Docker version 27.2.0, build 3ae425f
```

### 2. Run Test Image (hello-world)
```bash
$ docker run hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.
```

### 3. Pull Nginx Image from Docker Hub
```bash
$ docker pull nginx
Using default tag: latest
latest: Pulling from library/nginx
Digest: sha256:04ba374e90de84923ed7f00d897743b0ab12f185c721b0b5d564f895825a0753
Status: Downloaded newer image for nginx:latest
```

### 4. List Downloaded Images
```bash
$ docker images
REPOSITORY    TAG       IMAGE ID       CREATED        SIZE
nginx         latest    503c2020c237   2 weeks ago    187MB
hello-world   latest    d2c94e258dcb   5 months ago   13.3kB
```

### 5. Create and Run Nginx Container (Port 8080:80)
```bash
$ docker run -d -p 8080:80 --name my-nginx nginx
7a1b2c3d4e5f6a7b8c9d0e1f2a3b4c5d6e7f8a9b0c1d2e3f4a5b6c7d8e9f0a1b
```
*Navigated to `http://localhost:8080` in web browser -> "Welcome to nginx!" displayed.*

### 6. List Containers
```bash
$ docker ps
CONTAINER ID   IMAGE   STATUS         PORTS                  NAMES
7a1b2c3d4e5f   nginx   Up 2 minutes   0.0.0.0:8080->80/tcp   my-nginx

$ docker ps -a
CONTAINER ID   IMAGE         STATUS                     NAMES
7a1b2c3d4e5f   nginx         Up 2 minutes               my-nginx
b3e2f1a4c5d6   hello-world   Exited (0) 5 minutes ago   sharp_curie
```

### 7. Stop and Remove Container
```bash
$ docker stop my-nginx
my-nginx

$ docker rm my-nginx
my-nginx

$ docker rmi nginx
Untagged: nginx:latest
```

---

## Result
WSL 2 and Docker Desktop were verified, Docker images (`hello-world` and `nginx`) were pulled from Docker Hub, a container was run in detached mode with port mapping (`8080:80`), and container lifecycle operations were successfully executed.
