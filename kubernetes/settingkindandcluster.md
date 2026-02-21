Here’s a **README.md** file you can use to document the 10 essential `kubectl` commands for exploring your kind cluster. It’s structured, clear, and ready to drop into your repo:

```markdown
# Kubernetes Cluster Exploration with kubectl

This guide covers 10 essential `kubectl` commands to explore and understand a Kubernetes cluster created using **kind** (`kind create cluster --config kind-config.yaml`).

---

## 1. Check Cluster Info
```bash
kubectl cluster-info
```
Displays the addresses of the Kubernetes control plane and core services (like CoreDNS). Confirms the cluster is running.

---

## 2. List All Nodes
```bash
kubectl get nodes -o wide
```
Shows nodes, their roles, status, IPs, and Kubernetes version. Useful to verify control-plane and worker nodes.

---

## 3. Describe a Node
```bash
kubectl describe node kind-control-plane
```
Provides detailed info about a node: labels, taints, allocatable resources, conditions, and running pods.

---

## 4. View All Namespaces
```bash
kubectl get namespaces
```
Lists system namespaces (`kube-system`, `default`, `kube-public`) and any custom ones. Helps organize workloads.

---

## 5. List Pods Across All Namespaces
```bash
kubectl get pods --all-namespaces
```
Shows system pods (CoreDNS, kindnet, etc.) and user workloads. Confirms cluster services are healthy.

---

## 6. Check Current Context
```bash
kubectl config current-context
```
Displays the active context (cluster + user + namespace). With kind, you’ll typically see `kind-kind`.

---

## 7. List All Contexts
```bash
kubectl config get-contexts
```
Shows all clusters configured in your kubeconfig. Useful if you manage multiple clusters (kind, minikube, cloud).

---

## 8. Switch Context
```bash
kubectl config use-context kind-kind
```
Switches to the desired cluster context. Ensures commands target the correct cluster.

---

## 9. View API Resources
```bash
kubectl api-resources
```
Lists all resource types supported (Pods, Deployments, Services, CRDs). Helps you know what objects you can create/manage.

---

## 10. Cluster Version Details
```bash
kubectl version --short
```
Shows client and server versions of Kubernetes. Confirms compatibility between your `kubectl` and kind cluster.

---

## 🧭 Summary
- **Cluster health** → `cluster-info`, `get nodes`, `describe node`
- **Workload visibility** → `get namespaces`, `get pods --all-namespaces`
- **Context management** → `current-context`, `get-contexts`, `use-context`
- **Capabilities check** → `api-resources`, `version`

Use these commands as your first drill when exploring a new cluster. They give you a complete picture of the environment, workloads, and configuration.
```

---

Would you like me to also create a **practice lab flow** (step‑by‑step exercises) where you run these commands in sequence and interpret the output — like a mini‑CKA drill? That way, you’ll not only have the README but also a guided hands‑on workflow.
