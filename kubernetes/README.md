Get node list.
 ```bash
kubectl get nodes
```

Information about cluster.
```bash
kubectl cluster-info
```

### Pods
Create and Run a pod.
```bash
kubectl run <POD_NAME> --image=<IMAGE_NAME> --port=<PORT>
```
List pods
```bash
kubectl get pods
```
Describe pods
```bash
kubectl describe pods
kubectl describe pod <POD_NAME>
```
Delete pod
```bash
kubectl delete pod <POD_NAME>
```

### Logs
View pod logs.
```bash
kubectl logs <POD_NAME>
```

### Execute code inside container
```bash
kubectl exec -it <POD_NAME> -- <COMMAND>
```

