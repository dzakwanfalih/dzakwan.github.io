---
title:  "NGOPREK DOCKER" 
permalink: /posts/2021/03/ngoprel-docker
date: 2021-03-31-00
---



<h1 align="center">
  <br>
  <a href="#"><img src="https://blog.chun.no/images/2014-06-01-docker.gif" alt="Markdownify" width="300"></a>
  <br>
  Ngoprek docker !
  <br>
</h1>



# Docker Playground 

This is one of the most frustrating things a developer can encounter when delivering an
application. Often, the issues that creep up are related to a library that the developer had on their machine, but it wasn't included in the distribution of the package. It may seem like an easy fix for this would be to include all the libraries alongside the release, but what if this release contains a newer library that overwrites the older version, which may be required for a different application? 

Developers need to consider their new releases, as well as any potential conflicts with
any existing software on the user's workstations. This often becomes a careful balancing
act that requires larger deployment teams to test the application on different system
configurations. It can also lead to additional rework for the developer or, in some extreme
cases, full incompatibility with an existing application.

##  Installing Docker on Ubuntu

Now that we have finished preparing everything, let's install Docker:

1. The first step is to update the package index by executing apt-get update:
   ```bash 
    Fuck ➜ sudo apt-get update 
   ```
2. Next, we need to add any packages that may be missing on the host system to allow HTTPS apt access:
    ```bash
    Fuck ➜  sudo apt-get install apt-transport-https ca-certificates
      curl gnupg-agent software-properties-common
    ```

3. To pull packages from Docker's repository, we need to add their keys. You can add
  keys by using the following command, which will download the gpg key and add it
  to your system:
    ```bash
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add –
    ```
4. Now, add Docker's repository to your host system:
   ```bash
   sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs)stable"
   ```    
5. With all the prerequisites completed, you can install Docker on your server:
   ```bash
   sudo apt-get update
   sudo apt-get install docker-ce docker-ce-cli containerd.io
   ```
6. Docker is now installed on your host, but like most new services, Docker is not
currently running and has not been configured to start with the system. To start
Docker and enable it on startup, use the following command:
    ```bash
    sudo systemctl enable docker && systemctl start docker
    ```
## Granting Docker permissions

In a default installation, Docker requires root access, so you will need to run all Docker commands as root. Rather than using sudo with every Docker command, you can add
your user account to a new group on the server that provides Docker access without
requiring sudo for every command.

If you are logged on as a standard user and try to run a Docker command, you will receive
an error:

```bash
Got permission denied while trying to connect to the
Docker daemon socket at unix:///var/run/docker.sock: Get
http://%2Fvar%2Frun%2Fdocker.sock/v1.40/images/json: dial unix
/var/run/docker.sock: connect: permission denied
```

To allow your user, or any other user you may want to add to execute Docker commands,
you need to create a new group and add the users to that group. The following is an
example command you can use to add the currently logged on user: 

```bash
sudo groupadd docker
sudo usermod -aG docker $USER
```
The first command creates the docker group, while the second command adds the user
account that you are currently logged in with to the docker group.

## Hello Word

you can test that it works by running the standard hello world image (note that we
do not require sudo to run the Docker command):

```
 Fuck ➜  Docker docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
b8dfde127a29: Pull complete 
Digest: sha256:308866a43596e83578c7dfa15e27a73011bdd402185a84c5cd7f32a88b501a24
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/

 Fuck ➜  Docker 

```

# Using the Docker CLI

The Docker command is what you will use to interact with the Docker
daemon. Using this single executable, you can do the following, and more:

Start and stop containers
• Pull and push images
• Run a shell in an active container
• Look at container logs
• Create Docker volumes
• Create Docker networks
• Prune old images and volumes

### Docker run
To run a container, use the docker run command with the provided image name.
Before executing a docker run command, you should understand the options you
can supply when starting a container.

```bash
 Fuck ➜  Docker docker run bitnami/nginx:latest
Unable to find image 'bitnami/nginx:latest' locally
latest: Pulling from bitnami/nginx
dcf0f8e07c79: Pull complete 
8f302c5b7ecb: Pull complete 
8476165c2149: Pull complete 
0461f09377bf: Pull complete 
3af937d15a6f: Pull complete 
90852c48f2e4: Pull complete 
2cae4b49364a: Pull complete 
6bed36c5d559: Pull complete 
79bf2847e08d: Pull complete 
234661d51ee4: Pull complete 
9dbecd618303: Pull complete 
Digest: sha256:21e62c889e791f895b036a22f2a938d3d2efb1f65d3cc0ba2f80b4c692df20ff
Status: Downloaded newer image for bitnami/nginx:latest
nginx 06:04:59.71 
nginx 06:04:59.71 Welcome to the Bitnami nginx container
nginx 06:04:59.71 Subscribe to project updates by watching https://github.com/bitnami/bitnami-docker-nginx
nginx 06:04:59.71 Submit issues and feature requests at https://github.com/bitnami/bitnami-docker-nginx/issues
nginx 06:04:59.72 
nginx 06:04:59.72 INFO  ==> ** Starting NGINX setup **
nginx 06:04:59.73 INFO  ==> Validating settings in NGINX_* env vars
nginx 06:04:59.74 INFO  ==> Initializing NGINX
nginx 06:04:59.75 INFO  ==> ** NGINX setup finished! **

nginx 06:04:59.77 INFO  ==> ** Starting NGINX **
```

### Running Docker Backround

Command: 

```bash
docker run bitnami/nginx:latest -d 
```

Output: 

```
Fuck ➜  Docker docker run -d bitnami/nginx:latest 
4f113af4980c172a3dceff242fc76582e2a43adb42b672fdceadac41bdc7dc33
```
By default, containers will be given a random name once they are started. In our previous
detached example, the container has been given the name. ```vigorous_greider```

```
Fuck ➜  Docker docker ps
CONTAINER ID   IMAGE                  COMMAND                  CREATED              STATUS              PORTS                NAMES
4f113af4980c   bitnami/nginx:latest   "/opt/bitnami/script…"   About a minute ago   Up About a minute   8080/tcp, 8443/tcp   vigorous_greider

```

### Docker PS 

Every day, you will need to retrieve a list of running containers or a list of containers
that have been stopped. The Docker CLI has an option called ps that will list all
running containers, or if you add an extra option to the ps command, all containers
that are running and have been stopped.

```
Fuck ➜  Docker docker ps
CONTAINER ID   IMAGE                  COMMAND                  CREATED          STATUS          PORTS                NAMES
4f113af4980c   bitnami/nginx:latest   "/opt/bitnami/script…"   26 minutes ago   Up 26 minutes   8080/tcp, 8443/tcp   vigorous_greider
```

This is helpful if the container you are looking for is currently running. What if the
container was stopped, or even worse, what if you started the container and it failed to
start and then stopped? You can view the status of all containers, including previously run containers, by adding the -a option to the docker ps command.

the running containers will show a running time; for example, Up
xx hours, or Up xx days. However, if the container has been stopped for any reason, the
status will show when it stopped

## docker start and stop  