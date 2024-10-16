Used the ansible playbook in this [repository](https://github.com/k3s-io/k3s-ansible) to setup k3s in all Respberry pis.

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
To expose pod to be accessible,
```bash
kubectl expose pod <POD_NAME> --type=NodePort --port=<PORT> --target-port=<PORT>
```
This creates a service in the pod's name. <br>
NodePort randomly assigns a port from 30000 to 32767. <br>
To see IP and port of pod
```bash
kubectl get service <SERVICE_NAME>
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

### View utilization
```bash
kubectl top pods
kubectl top pod <POD_NAME>
```

### Execute code inside container
```bash
kubectl exec -it <POD_NAME> -- <COMMAND>
```

> [!IMPORTANT]  
> Use `Deployments` for stateless apps and `StatefulSet` for statefull apps. 

## Components of Kube config file
Api Version, kind (service/deployment)
1. **Metadata**
2. **Specification**
3. **Status** : Automatically generated and added by kubernetes.

## Deployments
The container is specified in a `template` in the `.yaml` file.
The template has it's own `metadata` and `spec`. <br>
Give labels to pods always and In deployement match labels. 

## Kube services 
Used to give static IPs for pods. (Also acts as load balancer)
### Internal Service
Doesn't expose pods for external access. Acess only within Kube cluster.
### External Service
Expose pods for external access in the network.

## Kube Ingress
Kinda DNS for pods.

## ConfigMap and Secrets
To manage env variables and secrets in the cluster.

> [!IMPORTANT]  
> Any data entered in Secrets should be in base64 encoded format. <br>
> Use this command to encode. <br>
> ```bash
>  echo <VALUE_TO_ENCODE> | base64
> ```
> Use this to check if the encoded value is right. <br>
> ```bash
>  echo <VALUE_TO_DECODE> | base64 --decode
> ```

## Volumes
Attach directory to kubernetes cluster

## etcd
Process in master node, that holds status of all components at any time.

## Scaling deployments manually
To scale a deployment manually use the following command. 
```bash
kubectl scale deployment <DEPLOYMENT_NAMES> --replicas=<NO_OF_REPLICAS>
```
<br>
<div align="center">
 <img src="https://github.com/user-attachments/assets/9d3d98bb-0b8b-4ff9-84bf-0a3b3b31d115" width="800px"/>
</div>



