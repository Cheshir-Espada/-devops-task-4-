# Task 4 — Jenkins Installation and Configuration

## Objective

This task sets up a Jenkins environment for local Kubernetes using Minikube. The goal is to deploy Jenkins via Helm, validate its functionality, and automate job creation via Jenkins Configuration as Code (JCasC).

---

## Steps

### 1. Helm Installation & Verification
- Installed Helm via Homebrew
- Verified by deploying and removing Bitnami Nginx chart

### 2. Minikube Setup
- Installed and launched Minikube with Docker driver
- Ensured `storage-provisioner` is active for dynamic PV/PVC

### 3. Persistent Volume Claim (PVC)
- Successfully created and bound a test PVC
- Validated volume provisioning

### 4. Jenkins Deployment
- Deployed via Helm into `jenkins` namespace
- Used official Helm chart: `jenkins/jenkins`
- Exposed Jenkins via `kubectl port-forward`

### 5. Freestyle Job
- Created `hello-world` Freestyle job
- Build step: `echo "Hello world"`
- Verified successful execution in Console Output

### 6. Jenkins Configuration as Code (JCasC)
- Job stored in `jenkins-values.yaml`
- Helm upgrade applies config and auto-creates job

---

## Files Included

- `jenkins-values.yaml` — Helm values with JCasC block
- `README.md` — this file
- `all-namespaces.txt` — output of `kubectl get all --all-namespaces`
- `screenshots/` — folder with:
  - Jenkins dashboard
  - Console Output with Hello world
  - Job configuration UI

---

## Usage

To deploy Jenkins with auto-configured job:
```bash
helm upgrade --install jenkins jenkins/jenkins -n jenkins -f jenkins-values.yaml


