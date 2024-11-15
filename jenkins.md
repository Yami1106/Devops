# Installing Jenkins on AWS EC2 Instance

> **Note**: Refer to the official Jenkins documentation for additional details: [Installing Jenkins on AWS](https://www.jenkins.io/doc/tutorials/tutorial-for-installing-jenkins-on-AWS/)

1. **Create an EC2 Instance and Configure Security Group**
   - Launch a new EC2 instance with your preferred settings.
   - Configure the Security Group:
     - **SSH Rule**: Protocol: SSH, Source: Custom, IP: Enter your public IP with `/32` suffix (check [http://checkip.amazonaws.com/](http://checkip.amazonaws.com/)).
     - **Custom TCP Rule**: Port Range: 8080, Source: Use the same IP as above.

2. **Connect to the EC2 Instance Using PuTTY**
   - Open PuTTY and enter the **Public DNS** of your instance.
   - Under **SSH -> Auth**, select your instance’s `.ppk` file.
   - Connect to your EC2 instance.

3. **Install Jenkins**
   - Update system packages:
     ```bash
     sudo yum update -y
     ```
   - Add Jenkins repository:
     ```bash
     sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
     ```
   - Import the Jenkins key:
     ```bash
     sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
     ```
   - Upgrade system packages:
     ```bash
     sudo yum upgrade -y
     ```
   - Install Java 17 (Amazon Corretto):
     ```bash
     sudo dnf install java-17-amazon-corretto -y
     ```
   - Install Jenkins:
     ```bash
     sudo yum install jenkins -y
     ```
   - Enable Jenkins on boot:
     ```bash
     sudo systemctl enable jenkins
     ```
   - Start Jenkins service:
     ```bash
     sudo systemctl start jenkins
     ```
   - Check Jenkins service status:
     ```bash
     sudo systemctl status jenkins
     ```

4. **Configure Jenkins**
   - Open a browser and go to:
     ```
     http://<your_server_public_DNS>:8080
     ```
   - Retrieve the initial admin password:
     ```bash
     sudo cat /var/lib/jenkins/secrets/initialAdminPassword
     ```
   - Copy the password, paste it into Jenkins setup, and follow the on-screen instructions to complete the configuration.
