# Check if cluster is reachable
kubectl cluster-info

# List nodes and status
kubectl get nodes

# See detailed info for a node (capacity, conditions, etc.)
kubectl describe node <node-name>
# All pods in current namespace
kubectl get pods

# All pods in all namespaces
kubectl get pods -A

# Watch pods changing in real-time
kubectl get pods -w

# Detailed info + events for a pod
kubectl describe pod <pod-name>
# Logs for a pod with single container
kubectl logs <pod-name>

# If pod has multiple containers
kubectl logs <pod-name> -c <container-name>

# Follow logs live (like tail -f)
kubectl logs -f <pod-name>


# Get a shell inside the container
kubectl exec -it <pod-name> -- /bin/bash
# or if bash not available
kubectl exec -it <pod-name> -- /bin/sh

# List services
kubectl get svc

# Detailed service info
kubectl describe svc <service-name>

# Check which pods are behind a service
kubectl get endpoints <service-name>


# List ingress
kubectl get ingress

# Detailed info + events
kubectl describe ingress <ingress-name>


# Check controller pod status
kubectl get pods -n ingress-nginx

# Controller logs
kubectl logs -n ingress-nginx <nginx-controller-pod-name>

# All events in the cluster (sorted by time)
kubectl get events --sort-by=.metadata.creationTimestamp

# Events only in a namespace
kubectl get events -n default --sort-by=.metadata.creationTimestamp

--Run a temporary debug pod:
kubectl run debug-pod --image=busybox:latest -it --restart=Never -- /bin/sh
# DNS test
nslookup order-service.default.svc.cluster.local

# Port test
wget -qO- http://order-service:5003

kubectl delete pod debug-pod


kubectl describe pod <pod>
kubectl describe svc <svc>
kubectl describe ingress <ingress>
kubectl describe node <node>

