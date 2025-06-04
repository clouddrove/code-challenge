# 🧪 Kubernetes Administration Practical Exam: Private Docker Registry Deployment

**Objective**: Demonstrate your ability to provision a highly available Kubernetes cluster, deploy a private Docker registry with persistent storage, configure health checks, networking, and perform a rolling upgrade.
**Level**: Intermediate
**Tools**: kubectl, kube-provisioning tool, YAML, Docker, Helm (optional), CronJob, AWS (or cloud provider of choice)

---

## 📄 Scenario

You have been assigned to set up and maintain a private Docker registry inside a Kubernetes environment. All resources must reside in a namespace called `clouddrove`. Your solution should ensure high availability, data durability, secure network access, and upgradeability. Provide only the required YAML manifests and/or CLI command sequences.

---

## ✅ Tasks

### Task 1: Cluster Setup

* Provision a regional Kubernetes cluster with **three worker nodes** spread across **three distinct availability zones**.
* Verify that both control-plane and worker nodes cover at least three AZs to ensure resilience.

📦 **Deliverable**:

* CLI commands or configuration snippets used to create the cluster.
* Confirmation (e.g., `kubectl get nodes -o wide`) showing AZ distribution.

---

### Task 2: Namespace Creation

* Create a namespace named `clouddrove`.
* Switch your context to the `clouddrove` namespace for all subsequent tasks.

📦 **Deliverable**:

* YAML or `kubectl` commands:

  ```bash
  kubectl create namespace clouddrove
  kubectl config set-context --current --namespace=clouddrove
  ```

---

### Task 3: Registry Deployment

* Deploy a Deployment resource named `registry-clouddrove` using image `registry:2.8.2` with **three replicas**.
* Use pod anti-affinity rules so that each replica schedules on a different node.

📦 **Deliverable**:

* `deployment-registry.yaml` containing the Deployment spec with `.spec.replicas: 3` and anti-affinity under `.spec.template.spec.affinity`.

---

### Task 4: Pre-Startup Initialization

* Add an `initContainer` (using an Alpine image) to the Deployment that ensures the directory `/var/lib/clouddrove` exists before the main container starts.

📦 **Deliverable**:

* The `initContainer` section in `deployment-registry.yaml` showing creation of `/var/lib/clouddrove` and mounting of the PVC.

---

### Task 5: Durable Storage

* Define a 50 Gi PersistentVolume (PV) and a matching PersistentVolumeClaim (PVC).
* Mount the PVC at `/var/lib/clouddrove` in each registry pod to persist data across restarts.

📦 **Deliverable**:

* `persistent-volume.yaml` and `persistent-volume-claim.yaml` files with 50 Gi storage request and appropriate access modes.
* Volume and volumeMount entries in `deployment-registry.yaml`.

---

### Task 6: Resource Management

* Configure the registry container’s resource requests and limits:

  * **requests**: `memory: "1Gi"`
  * **limits**: `memory: "2Gi"`

📦 **Deliverable**:

* The `.resources` section in `deployment-registry.yaml` under the registry container.

---

### Task 7: Readiness & Liveness Probes

* Add a `readinessProbe` for TCP port 5000 with:

  * `initialDelaySeconds: 15`
  * `periodSeconds: 30`
* Ensure failing probes cause the pod to restart automatically.

📦 **Deliverable**:

* `readinessProbe` (and optionally `livenessProbe`) configuration in `deployment-registry.yaml` for port 5000.

---

### Task 8: External Access

* Expose the registry pods via a Service of type `LoadBalancer`, mapping external port 5000 to the container’s port 5000.

📦 **Deliverable**:

* `service-registry.yaml` with `type: LoadBalancer`, `port: 5000`, and selector matching `registry-clouddrove`.

---

### Task 9: Network Controls

* Create a `NetworkPolicy` that:

  1. Allows ingress only on TCP port 5000 from pods within the `clouddrove` namespace.
  2. Denies all other ingress and egress traffic by default.

📦 **Deliverable**:

* `network-policy.yaml` containing a policy that matches `app: registry` pods and restricts traffic accordingly.

---

### Task 10: Configurations & Secrets

* Store any registry configuration settings (e.g., garbage-collection flags) in a `ConfigMap`.
* If registry authentication is required, place credentials in a Docker-registry `Secret`.

📦 **Deliverable**:

* `configmap-registry.yaml` with necessary environment variables or config files.
* `secret-registry.yaml` with `type: kubernetes.io/dockerconfigjson`.

---

### Task 11: Data Backup Plan

* In comments or annotations within your YAML, describe how to snapshot or back up the PVC (for example, using VolumeSnapshots or `kubectl cp`).
* Provide a `CronJob` manifest that periodically archives the contents of `/var/lib/clouddrove` to an external storage bucket (e.g., AWS S3 or equivalent).

📦 **Deliverable**:

* Comments/annotations in `persistent-volume-claim.yaml` or `deployment-registry.yaml` explaining the backup approach.
* `cronjob-backup.yaml` that runs at a regular interval and copies `/var/lib/clouddrove` to a remote bucket.

---

### Task 12: Rolling Upgrade

* List and execute the commands to:

  1. Cordon and drain one worker node.
  2. Upgrade that node to the next major Kubernetes version (e.g., from v1.24 to v1.25).
  3. Uncordon the node and verify all pods and nodes are healthy.

📦 **Deliverable**:

* Sequence of CLI commands to drain, upgrade, and uncordon nodes (e.g., `kubectl drain NODE_NAME --ignore-daemonsets`, `kubeadm upgrade node`, `kubectl uncordon NODE_NAME`).
* `kubectl get nodes` and `kubectl get pods -n clouddrove` output confirming health post-upgrade.

---

## 📂 Submission Checklist

* [ ] `deployment-registry.yaml`
* [ ] `persistent-volume.yaml`
* [ ] `persistent-volume-claim.yaml`
* [ ] `service-registry.yaml`
* [ ] `network-policy.yaml`
* [ ] `configmap-registry.yaml`
* [ ] `secret-registry.yaml` (if required)
* [ ] `cronjob-backup.yaml`
* [ ] CLI commands or comments for cluster provisioning (Task 1)
* [ ] CLI commands for rolling upgrade (Task 12)

---

## 💡 Notes

* You may use cloud-specific CLI commands (e.g., `gcloud`, `az`, `eksctl`) to provision and upgrade clusters.
* Test your YAML locally with `kubectl apply -f <file> --dry-run=client` before applying.
* Ensure your backup CronJob includes proper credentials for the external bucket.
* Label all resources with `app=registry` and `environment=dev` for easy identification.
* Clean up any resources after validation to avoid unwanted charges.

---
