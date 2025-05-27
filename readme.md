# Kubernetes Commands Cheat Sheet

## Cluster Management
```bash
# Create a new local cluster using kind
kind create cluster

# Delete the local cluster
kind delete cluster

# View cluster nodes
kubectl get nodes
```

## Pod Management
```bash
# Create a pod running nginx
kubectl run --image nginx

# Create a pod named 'giropops' running nginx on port 80
kubectl run --image nginx --port 80 giropops

# Access pod's shell
kubectl exec -ti giropops -- bash

# Delete a pod
kubectl delete pods giropops

# Generate pod manifest without creating it (dry run)
kubectl run --image nginx --port 80 giropops --dry-run=client
```

## Service Management
```bash
# Expose pod as a service (default type: ClusterIP)
kubectl expose pods giropops

# Expose pod as a NodePort service
kubectl expose pods giropops --type NodePort

# Delete a service
kubectl delete service giropops
```

## Resource Inspection
```bash
# List pods in kube-system namespace
kubectl get pods -n kube-system

# List pods in kube-system namespace with additional details
kubectl get pods -n kube-system -o wide

# List pods across all namespaces
kubectl get pods -n kube-system -A

# List deployments across all namespaces
kubectl get deployment -A

# List replicasets across all namespaces
kubectl get replicaset -A
```

## Configuration and Utilities
```bash
# Get help for kubectl completion
kubectl completion --help

# Apply or create resources from YAML file
kubectl apply/create -f pod.yaml
```

## Notes
- Use `kubectl` or `k` as shorthand for kubectl commands
- The `-A` or `--all-namespaces` flag shows resources across all namespaces
- Use `--dry-run=client` to generate manifests without applying them