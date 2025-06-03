# 🧪 DevOps Practical Exam: Docker + Terraform + Azure CLI

**Objective**: Create a portable environment using Docker to deploy infrastructure on Azure using Terraform.

**Duration**: 45–60 Minutes  
**Level**: Intermediate  
**Tools**: Docker, Terraform, Azure CLI, Bash, Azure Account

---

## 📄 Scenario

You are tasked with creating a Dockerized environment that installs Terraform and Azure CLI, mounts a Terraform file from the host, and deploys Azure resources from within the container.

---

## ✅ Tasks

### Task 1: Docker Image Preparation 

1. Pull the latest Ubuntu image from Docker Hub.  
2. Create a `Dockerfile` that:
   - Uses `ubuntu:latest` as base
   - Installs Terraform
   - Installs Azure CLI
   - Installs required tools: `curl`, `unzip`, `apt-transport-https`, `gnupg`, etc.

📦 **Deliverable**: `Dockerfile`

---

### Task 2: Build and Run the Container 

1. Build the Docker image and tag it as `terraform-azure-env`.  
2. Run a container from this image:
   - Mount a local volume containing `main.tf`
   - Set the working directory to `/workspace`
   - Make the Terraform CLI available

📦 **Deliverables**:
- `docker build` and `docker run` commands
- Screenshot of the container running

---

### Task 3: Terraform Deployment 

1. Create a `main.tf` file locally to deploy:
   - An Azure resource group named `devops-test-rg` in `eastus`

2. Inside the container:
   - Use `az login` to authenticate
   - Run `terraform init`
   - Run `terraform plan` and `terraform apply` to deploy the resource

📦 **Deliverables**:
- `main.tf`
- Screenshot of `terraform apply`
- Azure Portal screenshot showing the deployed resource

---

### Task 4: Automation & Cleanup

1. Modify the `Dockerfile` to automatically run Terraform if `.tf` files exist in `/workspace`.  
2. Add a `CMD` or `ENTRYPOINT` to simplify usage.  
3. Run `terraform destroy` to clean up resources.

📦 **Deliverables**:
- Updated `Dockerfile`
- Screenshot of cleanup (`terraform destroy`)

---

## 📂 Submission Checklist

- [ ] `Dockerfile`
- [ ] `main.tf`
- [ ] Screenshot of container running
- [ ] Screenshot of `terraform apply` output
- [ ] Azure Portal screenshot showing the resource group
- [ ] Screenshot of `terraform destroy`
- [ ] `docker build` and `docker run` commands used


---

## 💡 Notes

- You may use `az login --use-device-code` if browser access is unavailable inside the container.
- You must have an active Azure subscription to complete the deployment task.
- Consider using `.dockerignore` to keep your build clean.
