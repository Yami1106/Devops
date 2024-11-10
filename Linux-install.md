# Setting Up an EC2 Instance with HTTP and HTTPS Access

Follow these steps to launch an EC2 instance, configure HTTP/HTTPS access, and connect using PuTTY.

## Step 1: Launch an EC2 Instance
1. Go to the AWS Management Console.
2. Launch a new EC2 instance, selecting your desired AMI, instance type, and other settings.

## Step 2: Enable HTTP and HTTPS Access
1. Configure the security group to allow inbound HTTP (port 80) and HTTPS (port 443) traffic.
2. Create a new key pair and download the `.pem` file for secure access.

## Step 3: Wait for the Instance to Start

## Step 4: Install PuTTYgen
1. Download and install [PuTTYgen](https://www.puttygen.com/) on your local machine.
2. Open PuTTYgen.

## Step 5: Convert the `.pem` File to a `.ppk` File
1. Click on **Load** and select the `.pem` file downloaded in Step 2.
2. Click **Save private key** and give it a name to save as a `.ppk` file.

## Step 6: Configure PuTTY with the Private Key
1. Open PuTTY.
2. Under **Connection** > **SSH** > **Auth**, click **Browse** to select the `.ppk` file you saved in the previous step.

## Step 7: Connect to the EC2 Instance
1. In PuTTY, go to **Session** and enter the **Public IP** of your EC2 instance.
2. Click **Open** to initiate the connection.

## Step 8: Log in and Install Apache HTTP Server
1. Log in as `ec2-user` (or the default user for your AMI).
2. Run the following commands to install and start the Apache server:
   ```bash
   sudo yum install httpd -y
   sudo service httpd start
