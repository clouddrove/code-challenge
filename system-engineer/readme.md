# 🧪 System Engineer Practical Exam: Linux, Cloud CLI, Docker, Ansible & Networking

**Objective**: Validate your core system engineering skills—user management, package automation, AWS CLI operations, log analysis, container deployment, web server setup, Git workflows, Ansible ad-hoc commands, backup scripting, DNS troubleshooting, and firewall configuration.  
**Level**: Intermediate  
**Tools**: Linux CLI (bash), AWS CLI, Docker, Nginx, Git, Ansible, iptables/ufw  

---

## 📄 Scenario

You are a System Engineer responsible for maintaining a Linux-based environment with cloud integration, containerized services, automation via Ansible, and networking/security best practices. Complete each task by providing the exact commands, scripts, or configuration snippets required. Each task should be achievable (or clearly outlined) within a few minutes.

---

## ✅ Practical Tasks

### Task 1: User & Permission Management  
- Create a Linux user named `deploy`.  
- Add `deploy` to the `www-data` group.  
- Configure the home directory (`/home/deploy`) so that only members of `www-data` can read and write.  

📦 **Deliverable**:  
- Bash commands to add the user, assign group membership, and set directory permissions.

---

### Task 2: Package Installation Automation  
- Write a Bash one-liner (or short script) that:  
  1. Installs `nginx`.  
  2. Enables `nginx` to start on boot.  
  3. Verifies that the `nginx` service is active.  

📦 **Deliverable**:  
- Exact Bash command(s) to install, enable, and check `nginx`.

---

### Task 3: Cloud Resource Check  
- Using the AWS CLI, list all EC2 instances in the `us-east-1` region.  
- Output only each instance’s **Instance ID** and **State**.  

📦 **Deliverable**:  
- AWS CLI command producing a table or JSON with instance IDs and states.

---

### Task 4: Log File Analysis  
- Tail the last 50 lines of `/var/log/syslog`.  
- Filter entries containing the term “error” (case-insensitive).  
- Count how many such “error” entries occurred in the past hour.  

📦 **Deliverable**:  
- Bash command(s) chaining `tail`, `grep`, and `wc -l` (or equivalent) to display the count.

---

### Task 5: Docker Container Deployment  
- Pull the official `nginx:latest` image.  
- Run the container in detached mode, mapping host port 8080 to container port 80.  
- Provide the command that confirms the container is listening on port 8080.  

📦 **Deliverable**:  
- `docker pull` and `docker run` commands, plus the command (`docker ps` or `ss -tlnp`) verifying the listening port.

---

### Task 6: Web Server Configuration  
- Create an Nginx virtual host to serve a static site from `/var/www/html/site`.  
- Configure it to respond to requests for `test.local`.  
- Include only the essential lines of the `server { … }` block—no extra comments or directives.  

📦 **Deliverable**:  
- Snippet of the `server { … }` block to place in `/etc/nginx/sites-available/test.local`.

---

### Task 7: Git Repository Setup  
- Initialize a new Git repository in `/opt/project`.  
- Create a `README.md` file inside that directory.  
- Commit the `README.md` with the message “Initial commit.”  
- Show the Git log entry for that commit.  

📦 **Deliverable**:  
- Git commands (`git init`, `git add`, `git commit`) and the output of `git log -1`.

---

### Task 8: Service Restart Automation  
- Write an Ansible ad-hoc command that restarts the `nginx` service on all hosts in the `webservers` inventory group.  

📦 **Deliverable**:  
- The exact `ansible` command (including inventory path) used to restart `nginx` on `webservers`.

---

### Task 9: Backup & Rotation Script  
- Write (or pseudocode) a Bash script that:  
  1. Archives `/var/www` into a timestamped tarball (e.g., `www-YYYYMMDD-HHMMSS.tar.gz`).  
  2. Moves the tarball to `/backups`.  
  3. Keeps only the last **7** backups in `/backups`, deleting older files.  

📦 **Deliverable**:  
- Bash script content or annotated pseudocode showing each step and cleanup logic.

---

### Task 10: DNS Troubleshooting  
- A service at `web.example.com` cannot resolve `api.example.com`.  
- Describe (or provide commands) how to:  
  1. Inspect `/etc/resolv.conf` for DNS server settings.  
  2. Use `dig` or `nslookup` to test DNS resolution for `api.example.com`.  
  3. Identify and fix a misconfiguration (e.g., incorrect DNS server, missing A record).  

📦 **Deliverable**:  
- Sequence of troubleshooting commands and a brief note on the corrective action.

---

## 📂 Submission Checklist

- [ ] Bash commands for user creation, group assignment, and permission setup  
- [ ] Bash one-liner/script for installing and verifying `nginx`  
- [ ] AWS CLI command listing EC2 instance IDs and states  
- [ ] Bash commands for log analysis and “error” count  
- [ ] Docker commands for pulling, running, and verifying the `nginx` container  
- [ ] Nginx `server { … }` block snippet for `test.local`  
- [ ] Git commands and output for repository initialization  
- [ ] Ansible ad-hoc command to restart `nginx` on `webservers`  
- [ ] Bash script/pseudocode for `/var/www` backup and rotation  
- [ ] DNS troubleshooting commands and fix description  

---

## 💡 Notes

- Test Nginx configuration with `nginx -t` before reloading the service.  
- Use `aws configure` to set up AWS CLI credentials.  
- Verify Docker port mappings with `docker ps` or `ss -tlnp`.  
- Sample Ansible ad-hoc command:  
  ```bash
  ansible webservers -m service -a "name=nginx state=restarted" -i /path/to/inventory
