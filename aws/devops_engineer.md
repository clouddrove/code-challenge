# 🧪 DevOps Practical Exam: Containerized Microservice & Terraform Infrastructure

**Objective**: Build a minimal microservice, containerize it, publish the image, and provision cloud infrastructure to run it using Terraform.  
**Level**: Intermediate  
**Tools**: Docker, Terraform, Git, AWS

---

## 📄 Scenario

You are tasked with creating a simple microservice called **SimpleTimeService**, packaging it as a Docker container, and deploying the infrastructure required to run it in the cloud. All source code and Terraform configurations must be tracked in a public repository.

---

## ✅ Tasks

### Task 1: Build and Containerize a Minimal Microservice

**Service Name:** SimpleTimeService

1. **Application Development**  
   - Write a small web service in your preferred language (Go, Node.js, Python, C#, Ruby, etc.).  
   - On HTTP GET to `/`, return a JSON payload:
     ```json
     {
       "timestamp": "<current date and time>",
       "ip": "<client IP address>"
     }
     ```
2. **Dockerization**  
   - Create a `Dockerfile` that builds and runs SimpleTimeService.  
   - Ensure the container process runs as a non-root user.
3. **Image Publishing**  
   - Build the Docker image locally.  
   - Push the image to a public container registry (e.g., Docker Hub, GitHub Container Registry).
4. **Code Repository**  
   - Host all application source files and the `Dockerfile` in a public Git repository (GitHub, GitLab, Bitbucket, etc.).  
   - Verify that no sensitive data (API keys, credentials) is committed.

**Suggested Repository Structure**:  
```
/
├── src/                # Application source code  
├── Dockerfile          # Container build instructions  
└── README.md           # This file  
```


---

### Task 2: Provision Cloud Infrastructure with Terraform

Use Terraform to define and deploy the necessary AWS resources (or equivalent cloud provider) to host your containerized service. Choose one of the following options:

#### Option A: Server-Based Deployment

1. **Network Layout**  
   - Create a VPC with 2 public subnets and 2 private subnets.
2. **Compute Cluster**  
   - Provision an ECS (Elastic Container Service) or EKS (Elastic Kubernetes Service) cluster in the VPC.  
   - Ensure that worker nodes or ECS tasks run only in private subnets.
3. **Load Balancing**  
   - Deploy an Application Load Balancer (ALB) in the public subnets to route incoming traffic on port 80 (or 443) to your container service.

#### Option B: Serverless Deployment

1. **Network Layout**  
   - Create a VPC with 2 public subnets and 2 private subnets.
2. **Function as a Service**  
   - Package your SimpleTimeService container as a Lambda-compatible image (using AWS Lambda Container Support) or use an equivalent FaaS offering.  
   - Ensure the function runs in private subnets.
3. **Traffic Routing**  
   - Configure API Gateway, CloudFront, or a load balancer (e.g., ALB in Lambda mode) in public subnets to trigger your function on HTTP requests to `/`.

> 💡 **Tip:** You may use Terraform Registry modules (e.g., VPC module, ECS/EKS module) to accelerate your configuration.

---

## 📂 Submission Checklist

- [ ] **Repository Contents**  
  - Source code for SimpleTimeService under `src/`.  
  - `Dockerfile` at the repository root.  
  - Terraform configuration files (`main.tf`, `variables.tf`, `outputs.tf`, etc.) under a `terraform/` directory.
- [ ] **Docker Image**  
  - Docker image successfully built and pushed to a public registry (provide image reference in your README).
- [ ] **Terraform Code**  
  - Complete Terraform definitions for the chosen deployment option (server-based or serverless).
- [ ] **Usage Instructions**  
  - Clear steps in `README.md` for:  
    1. Cloning the repo  
    2. Building and pushing the Docker image  
    3. Initializing and applying Terraform  
    4. Verifying the deployed service endpoint
- [ ] **Cleanup Commands**  
  - Provide Terraform destroy commands and any additional steps to remove cloud resources.

---

## 💡 Notes

- Ensure that your application runs as a non-root user inside the container for better security.  
- Tag all Terraform-managed resources with a common `Environment = "DevOpsTest"` tag to facilitate cleanup.  
- For AWS CLI authentication inside Terraform, configure your credentials via `aws configure` or environment variables.  
- Verify network connectivity to your container service by obtaining the ALB or API Gateway endpoint after Terraform apply.  
- Always run `terraform plan` before `terraform apply` to review changes.  
- Destroy resources with `terraform destroy` and remove any leftover infrastructure to avoid ongoing cloud charges.

---
