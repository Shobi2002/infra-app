
---

## ⚙️ Deployment Flow (GitOps with Argo CD)

1. **App Repo** → Developers push code updates → GitHub Actions builds & pushes Docker image to registry.  
2. **Infra Repo (this repo)** → Manifests are updated automatically with the new image tag.  
3. **Argo CD** → Watches this repo and syncs changes to Kubernetes cluster.  
4. ✅ New version of the app runs automatically in the cluster.

---

## 📝 Manifests Overview

### Deployment
- Runs the container image: `shobanavijayan/app-repo:latest`
- Exposes port **80** inside the pod.
- Replica count: **1**

### Service
- Type: `ClusterIP` (can be changed to `NodePort` or `LoadBalancer` as needed).
- Exposes app on port **80** within the cluster.

---

## 🚀 Usage

Apply manifests manually (if not using Argo CD):
```bash
kubectl apply -f k8s/
