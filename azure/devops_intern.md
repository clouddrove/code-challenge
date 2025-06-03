# 🧪 DevOps Intern – Practical Assessment (⏱ 30–45 Minutes)

## 📌 Objective

Demonstrate your understanding of fundamental DevOps skills by provisioning cloud infrastructure, containerizing an application, and automating image deployment using CI/CD.

---

## 📋 Scenario

You have joined a DevOps team as an intern. Your task is to provision infrastructure on Azure, containerize a basic web app using Docker, and push the container image to Azure Container Registry (ACR) using an pipeline.

---

## ✅ Tasks

### 🔹 Task 1: Provision Azure Container Registry (ACR) using Terraform

- Create a Resource Group.
- Create an Azure Container Registry with `admin_enabled = true`.
- Use Terraform for infrastructure provisioning.
- Output the ACR login server at the end.


---

### 🔹 Task 2: Build a Simple Docker Image 

- Create a `Dockerfile` for a basic NGINX-based web server.
- Include a custom HTML page (e.g., "Hello from DevOps Intern").
- Test the image locally if time permits.

---

### 🔹 Task 3: Create Pipeline to Push Image to ACR 

- Use pipeline YAML file.
- Authenticate with ACR using a service connection.
- Build the Docker image and push it to ACR with a specific tag (e.g., `v1`).

---

## 📦 Deliverables

- `terraform/` directory with all Terraform code.
- `docker/` directory with `Dockerfile` and web content.
- `pipelines.yml` at project root.
- `README.md` explaining steps and project structure.
- Screenshots of:
  - Terraform apply output
  - Successful pipeline run
  - Image visible in ACR (via Azure CLI or portal)

---

## ⚠️ Notes

- Ensure your ACR name is lowercase and globally unique.
- Use best practices for folder structure and code clarity.
- Try to complete within 45 minutes.

---

## 🏁 Optional

- Tag Docker images using Git commit hash or build number.
- Add Terraform outputs for resource details.
- Include a simple test in the Docker image (optional).

---

## 🙌 Good Luck!
