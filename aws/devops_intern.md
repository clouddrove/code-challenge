
### 1. Linux User Setup  
Create a new user `intern`, add them to the `sudo` group, and configure `/etc/sudoers.d/intern` so they can run all commands without a password prompt.

---

### 2. Web Server Installation  
Write a Bash one-liner that installs `nginx`, starts the service, enables it at boot, and then verifies that it’s active.

---

### 3. Docker Container Listing  
List all running Docker containers, displaying only their container IDs and names.

---

### 4. Docker Container Deployment  
Pull the official `redis:latest` image, run it detached mapping container port 6379 to host port 6379, and show the command that confirms the container is listening.  

---

### 5. Cloud CLI Usage  
Use the AWS CLI to list all S3 buckets in your default region, outputting only the bucket names.  

---

### 6. Log Analysis  
Tail the last 100 lines of `/var/log/nginx/access.log`, filter entries from IP `127.0.0.1`, and count how many such requests occurred.

---

### 7. Git Workflow  
Initialize a Git repository in `/opt/intern-project`, create an empty `README.md`, commit with message “Initial commit”, and display the commit log entry.  

---

### 8. CI Pipeline Snippet  
Provide a minimal CI/CD Pipeline that checks out the repository and echoes “Hello, DevOps Intern!”.  

---

### 9. Monitoring Configuration  
Add a Prometheus `scrape_configs` section to `prometheus.yml` that scrapes `node_exporter` on `localhost:9100` every 15s.  

---

### 10. Configuration Management  
Run an Ansible ad-hoc command that pings all hosts in the `interns` group.  