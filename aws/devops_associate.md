# 🧪 DevOps Associate Practical Exam: Terraform, Docker Compose & Monitoring on AWS

**Objective**: Assess your ability to provision AWS resources with Terraform, orchestrate multi-service applications using Docker Compose, and configure monitoring and alerting.  
**Level**: Intermediate  
**Tools**: Terraform, AWS CLI, Docker, Docker Compose, GitHub, Prometheus

---

## 📄 Scenario

You have been hired as a DevOps Associate to build and maintain a small, cloud-native environment on AWS. You must:

- Use Terraform to create essential AWS infrastructure (S3, EC2).  
- Configure a local development environment with Docker Compose for a two-service application and log aggregation.  
- Implement monitoring and alerting for the AWS resources you provision.  

All configurations should follow best practices for versioning, observability, and rollback.

---

## ✅ Practical Tasks

### Task 1: Terraform S3 Bucket  
- Write a Terraform configuration (`s3.tf`) that provisions an S3 bucket named `devops-assoc-bucket` with versioning enabled.  
- **Deliverable**: `s3.tf` file (showing `resource "aws_s3_bucket"…versioning { enabled = true }`).  

---

### Task 2: EC2 Instance Provisioning  
- Create a Terraform configuration (`ec2.tf`) that launches a `t2.micro` EC2 instance in the default VPC.  
- Output the instance’s public IP address as a Terraform output variable.  
- **Deliverable**:  
  - `ec2.tf` file (including `aws_instance` resource and `output "public_ip" { … }`).  
  - Screenshot or CLI output showing the public IP.

---

### Task 3: CI Pipeline Snippet  
- Provide a minimal GitHub Actions workflow at `.github/workflows/ci.yml` that:  
  1. Checks out the repository.  
  2. Installs Terraform (e.g., using HashiCorp’s actions).  
  3. Runs `terraform validate` on your `.tf` files.  
- **Deliverable**: `.github/workflows/ci.yml` snippet.

---

### Task 4: Docker Compose Setup  
- Create a `docker-compose.yml` that defines two services:  
  1. **web**: A simple web application (you can use `nginx:alpine` or any basic HTTP server).  
  2. **redis**: Official `redis:latest` image.  
- Expose necessary ports (e.g., web on 8080, Redis on 6379) and set at least one environment variable for the web service (e.g., `ENV=dev`).  
- **Deliverable**: `docker-compose.yml` file.

---

### Task 5: Container Healthcheck  
- In your `docker-compose.yml`, add a `healthcheck` to the `web` service that:  
  - Runs every 30 seconds.  
  - Checks HTTP 200 on `http://localhost:8080/health`.  
- **Deliverable**: Updated `docker-compose.yml` showing the `healthcheck` section.

---

### Task 6: Log Aggregation  
- Extend `docker-compose.yml` (or create a new one) to include an ELK-style stack with three services:  
  1. **elasticsearch** (official image)  
  2. **logstash** (official image)  
  3. **kibana** (official image)  
- Provide the essential `logstash.conf` that:  
  - Reads logs from a mounted volume (assume path `/var/log/app.log`).  
  - Outputs to Elasticsearch on `http://elasticsearch:9200`.  
- **Deliverable**:  
  - `docker-compose.yml` with all four services (web, redis, elasticsearch, logstash, kibana).  
  - `logstash.conf` file.

---

### Task 7: CloudWatch Alert  
- Write an AWS CLI command (or JSON CloudFormation snippet) to create a CloudWatch alarm named `HighCPUAlarm` that:  
  - Monitors `CPUUtilization` of your EC2 instance.  
  - Triggers when CPU > 80% for 5 consecutive minutes.  
- **Deliverable**: AWS CLI command or JSON definition.

---

### Task 8: Service Monitoring  
- Update a Prometheus configuration (`prometheus.yml`) to scrape your EC2 instance every 15 seconds using `static_configs`. Assume the instance public IP is `X.X.X.X` and node exporter runs on port 9100.  
- **Deliverable**: `prometheus.yml` snippet showing:  
  ```yaml
  scrape_configs:
    - job_name: 'ec2_node'
      static_configs:
        - targets: ['X.X.X.X:9100']
      scrape_interval: 15s

---

## 📂 Submission Checklist

- [ ] `s3.tf`
- [ ] `ec2.tf`
- [ ] `.github/workflows/ci.yml`
- [ ] docker-compose.yml (initial & updated with healthcheck and ELK stack)
- [ ] `logstash.conf`
- [ ] AWS CLI command (or JSON) for CloudWatch alarm
- [ ] `prometheus.yml` snippet

---

## 💡 Notes
- Use aws configure to set up your AWS CLI credentials before running Terraform.

- Run `docker-compose up -d` locally to verify container healthchecks and log aggregation.

- Tag all Terraform resources with a common `Environment = "DevOpsTest"` tag for easy cleanup.

- Destroy any AWS resources (terraform destroy) and stop containers (docker-compose down) to avoid ongoing charges.

- If unable to create a CloudWatch alarm via CLI, you may provide a JSON CloudFormation template snippet instead.