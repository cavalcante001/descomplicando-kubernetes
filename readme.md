kind create cluster
kubectl get nodes
kind delete cluster
kubectl get pods -n kube-system
kubectl get pods -n kube-system -o wide
kubectl get pods -n kube-system -A
kubectl get deployment -A
kubectl get replicaset -A
kubectl completion --help 
kubectl run --image nginx
kubectl run --image nginx --port 80 giropops
kubectl exec -ti giropops -- bash
kubectl delete pods giropops
kubectl expose pods giropops
k delete service giropops   
kubectl expose pods giropops --type NodePort
kubectl run --image nginx --port 80 giropops --dry-run=client
kubtctl apply/create -f pod.yaml