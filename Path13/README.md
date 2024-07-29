# Docker 
Docker is an open-source platform designed to automate the deployment, scaling, and management of applications. It allows developers to package applications and their dependencies into a standardized unit called a container.

#### Key Components of Docker

1.  **Docker Engine**: The core component that runs and manages containers.
2.  **Docker Images**: Read-only templates used to create containers. They include everything needed to run an application, such as code, runtime, libraries, and environment variables.
3.  **Docker Containers**: Lightweight, standalone, and executable packages of software that include everything needed to run a piece of software, from the operating system to the application code.
4.  **Docker Hub**: A cloud-based repository where Docker users can create, test, store, and distribute container images.
#### Common Docker Commands

-   `docker run`: Run a container from an image.
-   `docker build`: Build an image from a Dockerfile.
-   `docker pull`: Pull an image from a repository.
-   `docker push`: Push an image to a repository.
-   `docker ps`: List running containers.
-   `docker stop`: Stop a running container.
-   `docker rm`: Remove a container.

      # FlowChart
      Docker  
---------------------------------
|      Docker ->Image 
 |                                              |
| Container1     Container2   |
|                                               |
|                                               |
                                          
---------------------------------

```sudo apt-get install -y docker.io```

``` sudo docker ps -a(Lists all containers)```

visit dockerhub.com

# Developing a ubuntu Docker

- search for ubuntu in dockerhub
- copy the pull command ```docker pull ubuntu```
-  we may add docker as sudo priviledged entity
- ``` sudo groupadd docker```
- ```sudo usermod -aG docker labuser```
-``` sudo systemctl restart docker```
-```sudo docker images```To view all images and containers
-```sudo docker run -it ubuntu bash```(-it = interactive shell, bash type)[starts a docker container]
- ```sudo docker exec -it dockerid /bin/bash```(To Execute the docker)
- ```sudo docker start dockerid```(to run the docker)


#Building Kali Linux Docker
- search for kali linux in dockerhub.com
- copy the pull command and paste in terminal
- remove junk images``` sudo docker rm containerid```
## Creating the yaml file
In shell scripting and command-line usage, `\` (backslash) and `&&` (double ampersand) serve different purposes:

### `\` (Backslash)

The backslash `\` is a line continuation character. It allows you to split a single command across multiple lines for better readability. When placed at the end of a line, it tells the shell that the command continues on the next line.


### `&&` (Double Ampersand)

The double ampersand `&&` is a logical AND operator. It allows you to chain commands together, ensuring that the next command runs only if the preceding command succeeds (returns an exit status of 0). This is useful for ensuring that dependent commands only execute if previous commands are successful.

```yaml
FROM kalilinux/kali-rolling
RUN apt-get update && \
         apt-get install -y \
         net-tools \
         nmap \
         sqlmap \
         hydra \
         openssh-server \
         apache2 \
         gobuster \
         john \
         sudo && \
         apt-get clean
 RUN useradd -m -s /bin/bash kalilinux && \
 echo 'kalilinux:kalilinux' | chpasswd && \
 echo 'kalilinux ALL=(ALL) NOPASSWD: ALL' >> /etc/sudoers
 RUN systemctl enable ssh && \
 systemctl enable apache2
EXPOSE 22 80 443
CMD service ssh start && \
service apache 2 start && \
/bin/bash
```

- ``` mkdir kali-docker```
- ``` cd kali-docker```
- ``` nano dockerfile```
- paste the yaml code into it
- ``` sudo docker -t kali-v1 . ```
- ``` sudo docker run -it -p 2222:22 
 -p 8080:80 -p 443:443 --name kali-v1-test1 kali-v1```
- -d to make it go in background
- binding machine ports with that of server
- Now connect to the docker using ssh machine
