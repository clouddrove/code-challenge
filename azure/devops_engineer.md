# 🧪 Azure DevOps Engineer Practical Test (⏱ 45 Minutes)

## 🎯 Objective
Automate the provisioning and deployment of a basic web application using **Terraform** and **Azure Pipelines**, simulating a real-world DevOps workflow.

---

## 📋 Scenario

You are tasked with:
- Creating a basic infrastructure on **Azure** using **Terraform**
- Building and deploying a sample web application to **Azure App Service** using **Azure Pipelines**


---

## ✅ Tasks

### 🔹 Task 1: Terraform Infrastructure (20 min)

Provision the following Azure resources:
- A **Resource Group**
- A **Linux App Service Plan** (SKU: `B1`)
- An **Azure Web App** (Runtime: Node.js 18(or above) or Python 3.11(or above))

**Deliverables:**
- `main.tf`, `variables.tf`, `terraform.tfvars`
- Use **local state**
- Output the Web App name or URL using Terraform output

---

### 🔹 Task 2: Azure Pipeline Configuration 

Create an Azure DevOps pipeline (`azure-pipelines.yml`) that:

- Triggers on push to the `main` branch
- Runs on a `ubuntu-latest` Microsoft-hosted agent
- Contains **two stages**:
  1. **Terraform Apply**
     - Run `terraform init`, `plan`, and `apply`
  2. **Application Deployment**
     - Deploy the app to Azure Web App using:
       - `az webapp deployment source config-zip`, or
       - `AzureWebApp` deployment task

**Requirements:**
- Use pipeline variables (can be hardcoded or passed at top of YAML)

---

### 🔹 Task 3: Mini Documentation 

Create a `README.md` that includes:
- What the pipeline does
- How the application is deployed
- Where secrets should be stored in a production scenario

---

## 📦 Submission Instructions

Please submit the following files as a zipped folder or via a GitHub repository:

- Terraform code (`.tf` files)
- App source (minimal)
- `azure-pipelines.yml`
- `README.md`


## 🧰 Tools Allowed

- Azure CLI
- Terraform CLI
- VS Code or similar

---

Good luck!
