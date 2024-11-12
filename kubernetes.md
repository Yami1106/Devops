# Setting Up Kubernetes with Docker Desktop and Deploying NGINX

1. **Install Docker Desktop**
   - Download and install Docker Desktop from [Docker's official website](https://docs.docker.com/desktop/).

2. **Enable Kubernetes in Docker Desktop**
   - Open Docker Desktop.
   - Navigate to `Settings` > `Kubernetes`.
   - Enable Kubernetes by checking the box next to “Enable Kubernetes”.

3. **Verify Kubernetes Installation**
   - Open a terminal and verify that `kubectl` is available by running:
     ```bash
     kubectl version
     ```

4. **Create a Deployment**
   - Deploy an NGINX container using Kubernetes with the following command:
     ```bash
     kubectl create deployment nginx --image=nginx
     ```

5. **View the Deployment**
   - Check the deployment status by running:
     ```bash
     kubectl get deployments
     ```

6. **Expose the Deployment as a Service**
   - To expose the NGINX deployment, run:
     ```bash
     kubectl expose deployment nginx --port=80 --type=LoadBalancer
     ```

7. **Verify the Service is Running**
   - Confirm that the service is active:
     ```bash
     kubectl get services
     ```

8. **View NGINX in the Browser**
   - Open a browser and enter `localhost:80` to view the NGINX welcome page.

9. **Delete the Deployment**
   - When done, delete the deployment with:
     ```bash
     kubectl delete deployment nginx
     ```

