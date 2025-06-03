
### 1. Cluster Setup  
- Stand up a regional K8s cluster with **three worker nodes**, each located in a separate availability zone.  
- Verify that both control-plane and worker nodes cover at least **three distinct AZs** for resilience.

### 2. Namespace Creation  
- Create and switch to a namespace named `clouddrove` to isolate all registry components.

### 3. Registry Deployment  
- Launch a Deployment called `registry-clouddrove` using image `registry:2.8.2` with **three replicas**.  
- Enforce pod anti-affinity so each replica lands on a different node.

### 4. Pre-Startup Initialization  
- Include an initContainer (based on Alpine) to ensure the directory `/var/lib/clouddrove` exists before the main container starts.

### 5. Durable Storage  
- Define a 50 Gi PersistentVolume and a matching PersistentVolumeClaim.  
- Mount the claim at `/var/lib/clouddrove` so registry data outlives pod restarts.

### 6. Resource Management  
- Set memory **requests** to `1Gi` and **limits** to `2Gi` for the registry container.

### 7. Readiness & Liveness Probes  
- Add a readinessProbe checking TCP port 5000:  
  - `initialDelaySeconds: 15`  
  - `periodSeconds: 30`  
- Ensure that failing probes trigger automatic pod restarts.

### 8. External Access  
- Expose the pods via a Service of type `LoadBalancer`, mapping external port 5000 to the container’s port 5000.

### 9. Network Controls  
- Create a NetworkPolicy that:  
  1. Allows ingress only on TCP port 5000 from within the `clouddrove` namespace.  
  2. Denies all other ingress and egress by default.

### 10. Configurations & Secrets  
- Store any registry settings (e.g., garbage-collection flags) in a ConfigMap.  
- Place credentials (if required) in a Docker-registry Secret.

### 11. Data Backup Plan  
- In comments or annotations, describe how you would snapshot or back up the PVC (e.g., using VolumeSnapshots or `kubectl cp`).  
- Provide a CronJob manifest that periodically archives `/var/lib/clouddrove` to an external bucket (e.g., S3).

### 12. Rolling Upgrade  
- List the commands to cordon and drain one node, apply a **major version** upgrade, uncordon it, then confirm all nodes and workloads remain healthy.

