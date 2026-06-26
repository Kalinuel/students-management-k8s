# Student Management System - Kubernetes Project

A production-like 3-tier application deployed on Kubernetes.

## Architecture

## Resources Used

| Resource | Purpose |
|---|---|
| Namespace | Isolated environment |
| ConfigMap | App configuration |
| Secret | Sensitive data |
| Deployment | Frontend & Backend |
| StatefulSet | Database with stable storage |
| PersistentVolume | Physical storage |
| PersistentVolumeClaim | Storage request |
| Service | Internal communication |
| Ingress | External traffic routing |
| CronJob | Automated student report every Monday 8AM |

## Files

- `frontend-deployment.yaml` - Namespace, ConfigMap, Secret, PV, PVC, Frontend Deployment & Service, CronJob
- `backend-deployment.yaml` - Backend Deployment & Service
- `st-state.yaml` - StatefulSet & Headless Service
- `st-ingress.yaml` - Ingress routing

## How to Deploy

```bash
# Apply all resources
kubectl apply -f frontend-deployment.yaml
kubectl apply -f backend-deployment.yaml
kubectl apply -f st-state.yaml
kubectl apply -f st-ingress.yaml
```

## Verify

```bash
kubectl get all -n student-management
kubectl get pvc -n student-management
kubectl get ingress -n student-management
```

## Test Report Generator

```bash
kubectl create job test-report --from=cronjob/cronme -n student-management
kubectl logs -l job-name=test-report -n student-management
```

## Tech Stack

- Kubernetes
- Minikube
- nginx
- WSL2 Ubuntu
- VS Code

## Author

Emmanuel Okpe (Kali)
Cloud/DevOps Engineer | Linux · Docker · Kubernetes · AWS
