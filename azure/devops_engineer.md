# 🧪 DevOps Practical Exam: Docker + Terraform + Azure CLI

**Objective**: Automate the provisioning and deployment of a basic web application using **Terraform** and **Azure Pipelines**, simulating a real-world DevOps workflow.

---

## 📋 Scenario

You are tasked with:
- Creating a basic infrastructure on **Azure** using **Terraform**
- Building and deploying a sample web application to **Azure App Service** using **Azure Pipelines**


---

## ✅ Tasks

### Task 1: Terraform Infrastructure

1. Provision the following Azure resources:
   - A **Resource Group**
   - A **Linux App Service Plan** (SKU: `B1`)
   - An **Azure Web App** (Runtime: Node.js 18(or above) or Python 3.11(or above))
   - Azure container registry.

📦 **Deliverables**:
- `main.tf`, `variables.tf`, `terraform.tfvars` , `outputs.tf`
- Use **local state**
- Output the Web App name or URL using Terraform output

---

### Task 2: Dockerize a Basic App 

1. Create a `Dockerfile` for a simple nodejs application. 
2. Test it locally.

📦 **Deliverable**: 
- `Dockerfile` 
- Screen shot for local testing. 
---

### Task 3: Azure Pipeline Configuration 

Create an Azure DevOps pipeline (`azure-pipelines.yml`) that:
  - Deploy terraform resource to azure portal. 
  - Build Dockerfile and push it to azure acr. 
     - Tagging should be done according to build number. 
  - Update web app with latest image tag. 


**Requirements:**
- Use pipeline variables

📦 **Deliverables**:
- Pipeline Yaml
- Screen shot for pipeline run.

---

### Task 4: Mini Documentation 

Create a `README.md` that includes:
- What the pipeline does
- How the application is deployed
- Where secrets should be stored in a production scenario

---

## 📂 Submission Checklist

- [ ] `Dockerfile`
- [ ] `main.tf` , `tfvars` , `outputs.tf` , `variables.tf`
- [ ] Screenshot of running web app and site.
- [ ] Screenshot of `terraform apply` output
- [ ] Azure Portal screenshots showing all resources.
- [ ] Screen shot of successful pipeline run.
