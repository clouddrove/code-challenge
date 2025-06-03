## Practical Tasks

1. **Terraform S3 Bucket**  
   Write a Terraform configuration that creates an S3 bucket with versioning enabled.

---

2. **EC2 Instance Provisioning**  
   Use Terraform to provision a t2.micro EC2 instance in a default VPC and output its public IP.

---

3. **CI Pipeline Snippet**  
   Provide a minimal GitHub Actions workflow (`.github/workflows/ci.yml`) that checks out code, installs dependencies, and runs `terraform validate`.

---

4. **Docker Compose Setup**  
   Create a `docker-compose.yml` for a two-service app (e.g., web + Redis), exposing ports and setting environment variables.

---

5. **Container Healthcheck**  
   Add a Docker healthcheck to the web service in your Compose file that verifies HTTP 200 on `/health`.

---

6. **Log Aggregation**  
   Configure an ELK-style stack using Docker Compose: include Elasticsearch, Logstash, and Kibana services. Show the essential `logstash.conf`.

---

7. **CloudWatch Alert**  
   Write an AWS CLI command (or JSON) to create a CloudWatch alarm that triggers when CPUUtilization > 80% for 5 minutes.

---

8. **Service Monitoring**  
   Using Prometheus’s `static_configs`, add your EC2 instance to `prometheus.yml` for scraping node metrics every 15 s.

---

9. **Git Branch Workflow**  
   Initialize a Git repo, create and switch to branch `feature/terraform`, commit your Terraform files, then merge into `main` using a pull request.

---

10. **Rollback Plan**  
    Simulate a failed Terraform apply: show the commands to roll back to the previous state using `terraform state` or by reverting Git to the last stable commit.


