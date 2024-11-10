# Installing Terraform and Setting Up a Basic Project

Follow these steps to install Terraform on an EC2 instance, create a basic project, and run a sample configuration.


### Step 1: Update the System
```bash
sudo yum update -y
```

### Step 2: Install `wget` and `unzip`
```bash
sudo yum install -y wget unzip
```

### Step 3: Download Terraform

```bash
wget https://releases.hashicorp.com/terraform/1.9.2/terraform_1.9.2_linux_amd64.zip
```


### Step 4: Unzip the Terraform Package
```bash
unzip terraform_1.9.2_linux_amd64.zip
```

### Step 5: Move Terraform to a System Path
```bash
sudo mv terraform /usr/local/bin/
```


### Step 6: Verify the Terraform Installation
```bash
terraform --version
```

### Step 7: Create a Directory for Terraform Projects
```bash
mkdir -p terraform-projects
```

### Step 8: Navigate to the Project Directory
```bash
cd terraform-projects
```

### Step 9: Create `main.tf` and enter the following:

```bash
provider "null" {}

resource "null_resource" "example" {
  provisioner "local-exec" {
    command = "echo Hello, Terraform!"
  }
}
```

### Step 10: Initialize the Terraform Project
```bash
terraform init
```


### Step 11: Apply the Terraform Configuration
```bash
terraform apply
```

### Step 12: Confirm the Apply Action

### Step 13: Type 'yes' when prompted to confirm and apply the configuration.
