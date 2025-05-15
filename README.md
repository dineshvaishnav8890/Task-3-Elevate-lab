# 🚀 DevOps Task 3: Infrastructure as Code (IaC) with Terraform

## 📌 Objective

Provision a **local Docker container** (NGINX) using **Terraform** to understand and implement Infrastructure as Code (IaC) concepts.

---

## 🧰 Tools & Technologies Used

- [Terraform](https://www.terraform.io/)
- [Docker](https://www.docker.com/)
- [NGINX](https://www.nginx.com/)
- Ubuntu EC2 Instance (for execution environment)

---

## 📁 File Structure

terraform-docker-container/
├── main.tf # Terraform configuration
├── terraform.tfstate # Auto-generated Terraform state file
├── README.md # This file




---

## 🪜 Step-by-Step Workflow

### ✅ Step 1: Install Prerequisites

Ensure the following are installed on your system:

- Docker (installed and running)
- Terraform CLI

> On Ubuntu:
```bash
sudo apt update
sudo apt install -y docker.io
wget -O - https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install terraform





✅ Step 2: Create Terraform Configuration File (main.tf)

terraform {
  required_providers {
    docker = {
      source  = "kreuzwerker/docker"
      version = "~> 2.20.0"
    }
  }
}

provider "docker" {
  host = "unix:///var/run/docker.sock"
}

resource "docker_image" "nginx" {
  name         = "nginx:latest"
  keep_locally = false
}

resource "docker_container" "nginx" {
  name  = "my-nginx-container"
  image = docker_image.nginx.latest

  ports {
    internal = 80
    external = 8080
  }
}




✅ Step 3: Initialize Terraform


# terraform init




✅ Step 4: Preview the Plan


# terraform plan



✅ Step 5: Apply the Configuration


# terraform apply



✅ Step 6: Verify the Running Container

# docker ps


✅ Step 7: Inspect Terraform State

# terraform state list
# terraform show




✅ Step 8: Destroy the Infrastructure

# terraform destroy


