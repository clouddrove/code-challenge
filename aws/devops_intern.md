# 🧪 DevOps Intern Practical Exam: Linux, Docker, AWS CLI, Git, CI/CD & Monitoring

**Objective**: Evaluate your foundational DevOps skills through hands-on tasks involving user management, web server setup, Docker operations, AWS CLI usage, log analysis, Git workflows, CI/CD configuration, monitoring setup, and basic configuration management.  
**Level**: Beginner / Intermediate  
**Tools**: Linux CLI (bash), Docker, AWS CLI, Nginx, Git, Prometheus, Ansible  

---

## 📄 Scenario

As a DevOps Intern, you need to perform core system and cloud tasks on a Linux host. Each task should be completed (or clearly outlined) in under 3–5 minutes. Provide only the commands, scripts, or configuration snippets required to fulfill each requirement.

---

## ✅ Practical Tasks

### Task 1: Linux User Setup  
- Create a new Linux user named `intern`.  
- Add the user to the `sudo` group.  
- Create an `/etc/sudoers.d/intern` file that allows passwordless sudo for `intern`.  

📦 **Deliverable**:  
- Bash commands that add the user, assign the group, and configure the sudoers file.

---

### Task 2: Web Server Installation  
- Write a Bash one-liner that:  
  1. Installs `nginx`.  
  2. Starts the `nginx` service.  
  3. Enables `nginx` to start on boot.  
  4. Verifies that `nginx` is active.  

📦 **Deliverable**:  
- Exact Bash command(s) to accomplish these steps.

---

### Task 3: Docker Container Listing  
- List all running Docker containers, showing only their container IDs and names.  

📦 **Deliverable**:  
- The Docker command that filters and displays container IDs and names.

---

### Task 4: Docker Container Deployment  
- Pull the official `redis:latest` image.  
- Run the Redis container in detached mode, mapping container port 6379 to host port 6379.  
- Provide the command that confirms the container is listening on port 6379.  

📦 **Deliverable**:  
- `docker pull` and `docker run` commands.  
- Command (e.g., `docker ps` or `ss -tlnp`) to verify the listening port.

---

### Task 5: Cloud CLI Usage  
- Use the AWS CLI to list all S3 buckets in your default region.  
- Output only the bucket names.  

📦 **Deliverable**:  
- AWS CLI command that returns a list of bucket names.

---

### Task 6: Log Analysis  
- Tail the last 100 lines of `/var/log/nginx/access.log`.  
- Filter entries originating from IP `127.0.0.1`.  
- Count how many such requests occurred.  

📦 **Deliverable**:  
- Bash command(s) chaining `tail`, `grep`, and `wc -l` (or equivalent) to produce the count.

---

### Task 7: Git Workflow  
- Initialize a Git repository in `/opt/intern-project`.  
- Create an empty `README.md` file in that directory.  
- Commit the `README.md` with the message “Initial commit”.  
- Display the Git log entry for that commit.  

📦 **Deliverable**:  
- Git commands (`git init`, `git add`, `git commit`) and the output of `git log -1`.

---

### Task 8: CI Pipeline Snippet  
- Create a minimal CI/CD pipeline definition that:  
  1. Checks out the repository.  
  2. Echoes “Hello, DevOps Intern!”  

*(You may use GitHub Actions, GitLab CI, or another CI system of your choice.)*  

📦 **Deliverable**:  
- A YAML snippet named `ci.yml` (or equivalent) demonstrating the steps above.

---

### Task 9: Monitoring Configuration  
- Add a `scrape_configs` section to `prometheus.yml` that scrapes a local `node_exporter` at `localhost:9100` every 15 seconds.  

📦 **Deliverable**:  
- The `prometheus.yml` snippet showing:  
  ```yaml
  scrape_configs:
    - job_name: "node_exporter"
      static_configs:
        - targets: ["localhost:9100"]
      scrape_interval: 15s

---

### Task 10: Configuration Management
- Run an Ansible ad-hoc command that pings all hosts in the interns inventory group.

📦 **Deliverable**: 
- The exact ansible command (including inventory path) used to execute the ping.

---

## 📂 Submission Checklist
- [ ] Bash commands for creating `intern` user, adding to sudo, and configuring passwordless sudo

- [ ] Bash one-liner(s) for installing and verifying `nginx`

- [ ] Docker command for listing running containers (IDs and names)

- [ ] `docker pull` and `docker run` commands for Redis; command verifying listening port

- [ ] AWS CLI command listing all S3 bucket names

- [ ] Bash command(s) for log analysis of `/var/log/nginx/access.log`

- [ ] Git commands and `git log` output for repository setup

- [ ] CI pipeline YAML snippet (`ci.yml`) that echoes “Hello, DevOps Intern!”

- [ ] `prometheus.yml` snippet for scraping `node_exporter` every 15s

- [ ] Ansible ad-hoc command to ping `interns` hosts

---

## 💡 Notes
- You can test Nginx status with `systemctl status nginx` or `nginx -t`.
- Use `aws configure` to set up AWS CLI credentials before listing S3 buckets.
- Verify Docker port mappings with `docker ps` or ..
- Ansible ad-hoc example: `ansible interns -m ping -i /path/to/inventory`
- Ensure that all commands are executable on a standard Linux environment (Ubuntu/CentOS).