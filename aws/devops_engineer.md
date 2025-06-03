
---

### 1. User & Permission Management  
Create a new Linux user `deploy`, add it to the `www-data` group, and configure its home directory with permissions that allow web-server access only to that group.  

---

### 2. Package Installation Automation  
Write a Bash one-liner (or short script) that installs `nginx`, ensures the service is enabled at boot, and verifies its status.  

---

### 3. Cloud Resource Check  
Using the AWS CLI, list all EC2 instances in the `us-east-1` region and output only their instance IDs and states.  

---

### 4. Log File Analysis  
Tail the last 50 lines of `/var/log/syslog`, filter entries containing “error” (case-insensitive), and count how many such entries occurred in the past hour.  

---

### 5. Docker Container Deployment  
Pull the official `nginx:latest` image, run it detached on port 8080, and show the command that verifies the container is listening on that port.  

---

### 6. Web Server Configuration  
Configure an Nginx virtual host to serve a static site from `/var/www/html/site` on domain `test.local`. Include only the essential lines of the server block.  

---

### 7. Git Repository Setup  
Initialize a new Git repo in `/opt/project`, create a `README.md`, commit it with message “Initial commit,” and show the log of that commit.  

---

### 8. Service Restart Automation  
Write an Ansible ad-hoc command that restarts the `nginx` service on all hosts in the `webservers` inventory group.  

---

### 9. Backup & Rotation Script  
Write (or pseudocode) a Bash script that:  
1. Archives `/var/www` into a timestamped tarball.  
2. Moves it to `/backups`.  
3. Keeps only the last **7** backups, deleting older ones automatically.  

---

### 10. DNS Troubleshooting  
A service on `web.example.com` cannot resolve `api.example.com`. How would you trace and fix the DNS issue on a Linux host?  

---

### 11. Firewall Rules  
Write the `iptables` (or `ufw`) commands to allow incoming SSH (port 22) and HTTP (port 80) while blocking all other TCP traffic.  

---

