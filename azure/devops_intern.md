# 🧪 DevOps Intern Practical Assessment: Pipeline + Terraform + Docker

**Objective**: Demonstrate your understanding of fundamental DevOps skills by provisioning cloud infrastructure, containerizing an application, and automating image deployment using CI/CD.

**Level**: Intern
**Tools**: Docker, Terraform, Azure , Pipelines

---

## 📋 Scenario

You have joined a DevOps team as an intern. Your task is to provision infrastructure on Azure, containerize a basic web app using Docker, and push the container image to Azure Container Registry (ACR) using an pipeline.

---

## ✅ Tasks

### Task 1: Provision Azure Container Registry (ACR) using Terraform

1. Create a Resource Group.
2. Create an Azure Container Registry with `admin_enabled = true`.
3. Use Terraform for infrastructure provisioning.

📦 **Deliverables**:
- `main.tf`
- Screenshot of `terraform apply`
- Azure Portal screenshot showing the deployed resource


---

### Task 2: Build a Simple Docker Image 

1. Create a `Dockerfile` for a basic NGINX-based web server.
2. Include a custom HTML page (e.g., "Hello from DevOps Intern").

📦 **Deliverable**: `Dockerfile`
---

### Task 3: Create Pipeline to Push Image to ACR 

1. Use pipeline YAML file.
2. Authenticate with ACR.
3. Build the Docker image and push it to ACR with a specific tag (e.g., `v1`).

📦 **Deliverables**:
- `main.tf`
- Screenshot of **Pipeline Run**

---

## 📂 Submission Checklist

- [ ] `Dockerfile`
- [ ] `main.tf`
- [ ] `pipelines.yml`
- [ ] Screenshot of `terraform apply` output
- [ ] Azure Portal screenshot showing the resources and image present in ACR.
- [ ] Screen shot of successful pipeline run.

---

## ⚠️ Notes

- Ensure your ACR name is lowercase and globally unique.
- Use best practices for folder structure and code clarity.

---

## 🏁 Optional

- Tag Docker images using Git commit hash or build number.
- Screen Shot for `terraform outputs`.
