# Steps to Install and Run Docker with Nginx on Windows


### Step 1: Install Docker, Download and install Docker for Windows from the official Docker documentation:
link[https://docs.docker.com/desktop/setup/install/windows-install/]

### Step 2: Verify Docker Installation,Open a terminal or PowerShell and run the following command to check the Docker version:
```docker --version```

### Step 3: Pull the Nginx Docker Image,Download the Nginx image from Docker Hub using:
```docker pull nginx```

### Step 4: Run an Nginx Container,Start a container running Nginx, binding port 80 on the host to port 80 on the container:
```docker run -d -p 80:80 nginx```

### Step 5: List Running Containers,Check that the Nginx container is running by listing active containers:
```docker ps```

### Step 6: Stop the Nginx Container,Stop the running Nginx container by replacing <container-id> with the container's actual ID:
```docker stop <container-id>```

### Step 7: Remove the Stopped Container,Remove the Nginx container once it’s stopped:
```docker rm <container-id>```

> Note if doing it in ec2_instance follow the following steps:

1) copy:

```bash 
sudo yum update -y
```

2) install

```bash 
sudo yum install docker -y
```

3) start and enable

```bash 
sudo service docker start
sudo systemctl enable docker
```

4) add user to the group

```bash 
sudo usermod -aG docker ec2-user
```

5) pull image
```bash 
docker pull nginx
```

6) run image

```bash 
docker run -d -p 80:80 nginx
```

7) container status
```bash 
docker ps
```

8) stop container
```bash 
docker stop <container-id>
```

9) remove container
```bash 
docker rm <container-id>
```

