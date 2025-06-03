# Kubernetes Commands Cheat Sheet

## Day 1 - Basic Kubernetes Operations

### Cluster Management
```bash
# Create a new local cluster using kind
kind create cluster

# Delete the local cluster
kind delete cluster

# View cluster nodes
kubectl get nodes
```

### Pod Management
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

### Service Management
```bash
# Expose pod as a service (default type: ClusterIP)
kubectl expose pods giropops

# Expose pod as a NodePort service
kubectl expose pods giropops --type NodePort

# Delete a service
kubectl delete service giropops
```

### Resource Inspection
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

### Configuration and Utilities
```bash
# Get help for kubectl completion
kubectl completion --help

# Apply or create resources from YAML file
kubectl apply/create -f pod.yaml
```

### Notes
- Use `kubectl` or `k` as shorthand for kubectl commands
- The `-A` or `--all-namespaces` flag shows resources across all namespaces
- Use `--dry-run=client` to generate manifests without applying them

## Day 2 - Advanced Pod Operations

### Pod Inspection and Debugging
```bash
# Get detailed information about a pod
kubectl describe pods giropops

# Get pod configuration in YAML format
kubectl get pods -o yaml

# Get pods with specific label
kubectl get pods -L run

# Run interactive pods with different images
kubectl run girus --image busybox -ti
kubectl run girus-1 --image alpine -ti

# Install curl in Alpine pod
apk add curl

# Test connectivity to a pod IP
curl 10.244.2.4

# Attach to a running pod
kubectl attach girus-1 -c girus-1 -i -t

# Execute commands in pods
kubectl exec -ti strigus -- bash
kubectl exec strigus -- cat /usr/share/nginx/html/index.html

# Delete resources from YAML file
kubectl delete -f pod.yaml

# Watch pods in real-time
kubectl get pods -w

# View pod logs
kubectl logs girus
kubectl logs girus -c nginx
```