# Learning Notes - DevOps

`Learning Resources for DevOps, SRE, Cloud & Engineering Management`

[![BINPIPE](https://img.shields.io/badge/BINPIPE-YouTube-red)](https://www.youtube.com/channel/UCPTgt4Wo0MAnuzNEEZlk90A)
[![Learn DevOps!](https://img.shields.io/badge/BINPIPE-Learn--DevOps-orange)](https://github.com/BINPIPE/resources/blob/master/devops-lesson-plans.md)
[![BINPIPE](https://img.shields.io/badge/Live--Classroom-blue)](https://forms.gle/tDJxDyj2nJyfsgsk7)
---

# DOCKER ESSENTIALS



## **Docker Essentials**


### **Virtual Machines & Containers**

A **Virtual Machine** (VM) is a virtual environment that functions as a virtual computer system with its own CPU, memory, network interface, and storage, created on a physical hardware system. Software called a hypervisor separates the machine’s resources from the hardware and provisions them appropriately so they can be used by the VM. VMs allow multiple different operating systems to run simultaneously on a single computer.

* *Problems with VMs*
Virtualization has few drawbacks such as the virtual machines are bulky in size, running multiple virtual machines lead to unstable performance, boot up process would takes a long time and VM’s do not solve the problems like portability, software updates, or continuous integration and continuous delivery.

On the other hand, **Containers** are a form of operating system virtualization. A single container might be used to run anything from a small microservice or software process to a larger application. Inside a container are all the necessary executables, binary code, libraries, and configuration files. Compared to server or machine virtualization approaches, however, containers do not contain operating system images. This makes them more lightweight and portable, with significantly less overhead.

### **Docker**

**Docker** is a platform which packages an application and all its dependencies together in the form of containers (You can visualize a container as an isolated box). This containerization aspect of Docker ensures that the application works in any environment.

**Dockerfile**, **Docker Images** & **Docker Containers** are three important terms that you need to understand while using Docker.
 ```
             Build                  Run
Dockerfile --------> Docker Image ------> Docker Container
```

As you can see in the above diagram when the Dockerfile is built, it becomes a Docker Image and when we run the Docker Image then it finally becomes a Docker Container.

Refer below to understand all the three terms.

**Dockerfile:** A Dockerfile is a text document which contains all the commands that a user can call on the command line to assemble an image. So, Docker can build images automatically by reading the instructions from a Dockerfile. You can use  `docker build` to create an automated build to execute several command-line instructions in succession.

**Docker Image:**  In layman terms, Docker Image can be compared to a template which is used to create Docker Containers. So, these read-only templates are the building blocks of a Docker Container. You can use `docker run`  to run the image and create a container.

Docker Images are stored in the Docker Registry. It can be either a user’s local repository or a public repository like a Docker Hub which allows multiple users to collaborate in building an application.

**Docker Container:** Docker Container is a running instance of a Docker Image as they hold the entire package needed to run the application. So, these are basically the ready applications created from Docker Images which is the ultimate utility of Docker.

<hr>

### **Common Docker Commands**


Install Docker:

```
sudo apt-get remove docker docker-engine docker.io containerd runc
sudo apt install docker.io
sudo usermod -aG docker your-user
```


Create a container (without starting it):

```output
docker create [IMAGE]
```

Rename an existing container:

```output
docker rename [CONTAINER_NAME] [NEW_CONTAINER_NAME]
```

Run a command in a new container:

```output
docker run [IMAGE] [COMMAND]
```

`docker run --rm [IMAGE]`  – removes a container after it exits.

`docker run -td [IMAGE]`  – starts a container and keeps it running.

`docker run -it [IMAGE]`  – starts a container, allocates a pseudo-TTY connected to the container’s stdin, and creates an interactive bash shell in the container.

`docker run -it-rm [IMAGE]`  – creates, starts, and runs a command inside the container. Once it executes the command, the container is removed.

Delete a container (if it is not running):

```output
docker rm [CONTAINER]
```

Update the configuration of one or more containers:

```output
docker update [CONTAINER]
```

### Starting and Stopping Containers

Start a container:

```output
docker start [CONTAINER]
```

Stop a running container:

```output
docker stop [CONTAINER]
```

Stop a running container and start it up again:

```output
docker restart [CONTAINER]
```

Pause processes in a running container:

```output
docker pause [CONTAINER]
```

Unpause processes in a running container:

```output
docker unpause [CONTAINER]
```

Block a container until others stop (after which it prints their exit codes):

```output
docker wait [CONTAINER]
```

Kill a container by sending a SIGKILL to a running container:

```output
docker kill [CONTAINER]
```

Attach local standard input, output, and error streams to a running container:

```output
docker attach [CONTAINER]
```


### Docker Image Commands

Create an image from a Dockerfile:

```output
docker build [URL]
```

`docker build -t`  – builds an image from a Dockerfile in the current directory and tags the image

Pull an image from a registry:

```output
docker pull [IMAGE]
```

Push an image to a registry:

```output
docker push [IMAGE]
```

Create an image from a tarball:

```output
docker import [URL/FILE]
```

Create an image from a container:

```output
docker commit [CONTAINER] [NEW_IMAGE_NAME]
```

Remove an image:

```output
docker rmi [IMAGE]
```

Load an image from a tar archive or stdin:

```output
docker load [TAR_FILE/STDIN_FILE]
```

Save an image to a tar archive, streamed to STDOUT with all parent layers, tags, and versions:

```output
docker save [IMAGE] > [TAR_FILE]
```

### Docker Commands for Container and Image Information

Once you set up your containers, you will need to know how to get all the important information for managing them. The following commands will provide details on images and containers on your system.

**List running containers:**

```
docker ps
```

`docker ps -a`  – lists both running containers and ones that have stopped


**List the logs from a running container:**

```output
docker logs [CONTAINER]
```

**List low-level information on Docker objects:**

```output
**docker inspect [OBJECT_NAME/ID]**
```

**List real-time events from a container:**

```output
docker events [CONTAINER]
```

**Show port (or specific) mapping for a container:**

```output
docker port [CONTAINER]
```

**Show running processes in a container:**

```output
docker top [CONTAINER]
```

**Show live resource usage statistics of containers:**

```output
docker stats [CONTAINER]
```

**Show changes to files (or directories) on a filesystem:**

```output
docker diff [CONTAINER]
```

**List all images that are locally stored with the docker engine:**

```output
docker image ls
```

**Show the history of an image:**

```output
docker history [IMAGE]
```

**List networks:**

```output
docker network ls
```

**Remove one or more networks:**

```output
docker network rm [NETWORK]
```

**Show information on one or more networks:**

```output
docker network inspect [NETWORK]
```

**Connects a container to a network:**

```output
docker network connect [NETWORK] [CONTAINER]
```

**Disconnect a container from a network:**

```output
docker network disconnect [NETWORK] [CONTAINER]
```

<hr>

**HANDS-ON EXCERCISE**

**Creating a Static-Website App**

```
git clone https://github.com/BINPIPE/static-site-docker.git
cd BINPIPE/static-site-docker
chmod +x wrapper.sh
```
```script
docker build --tag binpipe/static-site-docker:1.0 .

```

```docker run -p 8888:80 binpipe/static-site-docker:1.0```


**Creating a Bulletin Board App**

If you are using Git, you can clone the example project from GitHub:

```
git clone https://github.com/dockersamples/node-bulletin-board
cd node-bulletin-board/bulletin-board-app

```

----------

The  `node-bulletin-board`  project is a simple bulletin board application, written in Node.js. In this example, let’s imagine you wrote this app, and are now trying to containerize it.

**Define a container with Dockerfile**

Take a look at the file called  `Dockerfile`  in the bulletin board application. Dockerfiles describe how to assemble a private filesystem for a container, and can also contain some metadata describing how to run a container based on this image. The bulletin board app Dockerfile looks like this:

```
# Use the official image as a parent image.
FROM node:current-slim

# Set the working directory.
WORKDIR /usr/src/app

# Copy the file from your host to your current location.
COPY package.json .

# Run the command inside your image filesystem.
RUN npm install

# Inform Docker that the container is listening on the specified port at runtime.
EXPOSE 8080

# Run the specified command within the container.
CMD [ "npm", "start" ]

# Copy the rest of your app's source code from your host to your image filesystem.
COPY . .

```

Writing a Dockerfile is the first step to containerizing an application. You can think of these Dockerfile commands as a step-by-step recipe on how to build up your image. This one takes the following steps:

-   Start  `FROM`  the pre-existing  `node:current-slim`  image. This is an  _official image_, built by the node.js vendors and validated by Docker to be a high-quality image containing the Node.js Long Term Support (LTS) interpreter and basic dependencies.
-   Use  `WORKDIR`  to specify that all subsequent actions should be taken from the directory  `/usr/src/app`  _in your image filesystem_  (never the host’s filesystem).
-   `COPY`  the file  `package.json`  from your host to the present location (`.`) in your image (so in this case, to  `/usr/src/app/package.json`)
-   `RUN`  the command  `npm install`  inside your image filesystem (which will read  `package.json`  to determine your app’s node dependencies, and install them)
-   `COPY`  in the rest of your app’s source code from your host to your image filesystem.

You can see that these are much the same steps you might have taken to set up and install your app on your host. However, capturing these as a Dockerfile allows you to do the same thing inside a portable, isolated Docker image.

The steps above built up the filesystem of our image, but there are other lines in your Dockerfile.

The  `CMD`  directive is the first example of specifying some metadata in your image that describes how to run a container based on this image. In this case, it’s saying that the containerized process that this image is meant to support is  `npm start`.

The  `EXPOSE 8080`  informs Docker that the container is listening on port 8080 at runtime.

What you see above is a good way to organize a simple Dockerfile; always start with a  `FROM`  command, follow it with the steps to build up your private filesystem, and conclude with any metadata specifications. There are many more Dockerfile directives than just the few you see above. For a complete list, see the  [Dockerfile reference](https://docs.docker.com/engine/reference/builder/).

**Build and test your image**

Now that you have some source code and a Dockerfile, it’s time to build your first image, and make sure the containers launched from it work as expected.

> **Windows users**: this example uses Linux containers. Make sure your environment is running Linux containers by right-clicking on the Docker logo in your system tray, and clicking  **Switch to Linux containers**  if the option appears. Don’t worry - all the commands in this tutorial work the exact same way for Windows containers.

Make sure you’re in the directory  `node-bulletin-board/bulletin-board-app`  in a terminal or PowerShell using the  `cd`  command. Let’s build your bulletin board image:

```script
docker build --tag bulletinboard:1.0 .

```

You’ll see Docker step through each instruction in your Dockerfile, building up your image as it goes. If successful, the build process should end with a message  `Successfully tagged bulletinboard:1.0`.

> **Windows users:**  you may receive a message titled ‘SECURITY WARNING’ at this step, noting the read, write, and execute permissions being set for files added to your image. We aren’t handling any sensitive information in this example, so feel free to disregard the warning in this example.

**Run your image as a container**

1.  Start a container based on your new image:

    ```script
    docker run --publish 8000:8080 --detach --name bb bulletinboard:1.0

    ```

    There are a couple of common flags here:

    -   `--publish`  asks Docker to forward traffic incoming on the host’s port 8000, to the container’s port 8080. Containers have their own private set of ports, so if you want to reach one from the network, you have to forward traffic to it in this way. Otherwise, firewall rules will prevent all network traffic from reaching your container, as a default security posture.
    -   `--detach`  asks Docker to run this container in the background.
    -   `--name`  specifies a name with which you can refer to your container in subsequent commands, in this case  `bb`.

    Also notice, you didn’t specify what process you wanted your container to run. You didn’t have to, as you’ve used the  `CMD`  directive when building your Dockerfile; thanks to this, Docker knows to automatically run the process  `npm start`  inside the container when it starts up.

2.  Visit your application in a browser at  `localhost:8000`. You should see your bulletin board application up and running. At this step, you would normally do everything you could to ensure your container works the way you expected; now would be the time to run unit tests, for example.

3.  Once you’re satisfied that your bulletin board container works correctly, you can delete it:

    ```script
    docker rm --force bb

    ```

    The  `--force`  option removes the running container. If you stop the container running with  `docker stop bb`  you do not need to use  `--force`.

<hr>


### **Container Orchestrators**

Below are some popular container orchestration tools.

**Docker Compose**  is a YAML file which contains details about the services, networks, and volumes for setting up the Docker application. So, you can use Docker Compose to create separate containers, host them and get them to communicate with each other. Each container will expose a port for communicating with other containers.

**Docker Swarm** is a technique to create and maintain a cluster of **Docker Engines**.  The Docker engines can be hosted on different nodes, and these nodes, which are in remote locations, form a Cluster when connected in Swarm mode.

**Kubernetes** is an open-source system for automating deployment, scaling, and management of containerized applications.” Kubernetes was built by Google based on their experience running containers in production using an internal cluster management system called [Borg](http://blog.kubernetes.io/2015/04/borg-predecessor-to-kubernetes.html) (sometimes referred to as Omega).

**Amazon ECS** is a highly scalable, high performance container management service that supports Docker containers and allows you to easily run applications on a managed cluster of Amazon **EC2** instances.


**Mesos-Marathon** [Mesos](http://mesos.apache.org/)  is a distributed kernel that aims to provide _dynamic allocation_ of resources in your datacenter. Imagine that you manage the IT department of a mid-size business. You need to have workloads running on 100 nodes during the day but on 25 after hours. Mesos can redistribute workloads so that the other 75 nodes can be powered-off when they are not used. Mesos can also provide resource sharing. In the event that one of your nodes fails, workloads can be distributed among other nodes. [Marathon](https://mesosphere.github.io/marathon/)  is a framework (or meta framework) that can launch applications and other frameworks. Marathon also serves as a container orchestration platform which can provide scaling and self-healing for containerized workloads.


Note: *Orchestrators are beyond the scope of coverage of this session. We have a separate masterclass session for each container orchestrator in-depth under `Advanced DevOps` lesson-plans.*



<pre>
<a href="https://www.binpipe.org">BINPIPE</a> aims to simplify learning for those who are looking to make a foothold in the industry.
Write to me at <b>nixgurus@gmail.com</b> if you are looking for tailor-made training sessions.
For self-study resources look around in this repository, <a href="https://www.binpipe.org/">the Binpipe Blog</a> and <a href="https://www.youtube.com/channel/UCPTgt4Wo0MAnuzNEEZlk90A">Youtube Channel</a>.
</pre>

___
:ledger: Maintainer: **[Prasanjit Singh](https://www.linkedin.com/in/prasanjit-singh)** | **www.binpipe.org**
___

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
