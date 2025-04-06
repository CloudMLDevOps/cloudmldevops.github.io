# Kubectl CheatSheet 2025

## Kubectl Command Cheatsheet

`kubectl` is the command-line interface for interacting with Kubernetes clusters. It allows you to deploy applications, inspect and manage cluster resources, and view logs. This cheatsheet provides a comprehensive reference of commonly used `kubectl` commands, organized by operation type.

Whether you're new to Kubernetes or an experienced administrator, this guide will help you quickly find the right command for your task. Commands are presented with their descriptions and practical examples to make your Kubernetes workflow more efficient.

## Cluster Management Commands

| Command                                 | Description                          | Example                                      |
|-----------------------------------------|--------------------------------------|----------------------------------------------|
| `kubectl cluster-info`                  | Display cluster info                 | `kubectl cluster-info`                       |
| `kubectl version`                       | Show kubectl and cluster version     | `kubectl version`                            |
| `kubectl config view`                   | Show kubeconfig settings             | `kubectl config view`                        |
| `kubectl config current-context`        | Display current context              | `kubectl config current-context`             |
| `kubectl config use-context <context>`  | Switch to another context            | `kubectl config use-context minikube`        |
| `kubectl config set-context`            | Set a context parameter              | `kubectl config set-context --current --namespace=myapp` |
| `kubectl api-resources`                 | List supported API resources         | `kubectl api-resources`                      |

## Namespace Operations

| Command                                              | Description               | Example                                       |
|------------------------------------------------------|---------------------------|-----------------------------------------------|
| `kubectl get namespaces`                             | List all namespaces       | `kubectl get ns`                              |
| `kubectl create namespace <name>`                    | Create a namespace        | `kubectl create ns app-dev`                   |
| `kubectl delete namespace <name>`                    | Delete a namespace        | `kubectl delete ns app-dev`                   |
| `kubectl config set-context --current --namespace=<ns>` | Set default namespace     | `kubectl config set-context --current --namespace=app-dev` |

## Pod Operations

| Command                                         | Description                                  | Example                                         |
|-------------------------------------------------|----------------------------------------------|-------------------------------------------------|
| `kubectl get pods`                              | List all pods in current namespace           | `kubectl get pods`                              |
| `kubectl get pods --all-namespaces`             | List pods in all namespaces                  | `kubectl get pods -A`                           |
| `kubectl get pods -o wide`                      | List pods with more details                  | `kubectl get pods -o wide`                      |
| `kubectl describe pod <pod-name>`               | Show detailed pod information                | `kubectl describe pod nginx-pod`                |
| `kubectl run <name> --image=<image>`            | Create and run a pod                         | `kubectl run nginx --image=nginx`               |
| `kubectl delete pod <pod-name>`                 | Delete a pod                                 | `kubectl delete pod nginx-pod`                  |
| `kubectl logs <pod-name>`                       | Get pod logs                                 | `kubectl logs nginx-pod`                        |
| `kubectl logs -f <pod-name>`                    | Stream pod logs                              | `kubectl logs -f nginx-pod`                     |
| `kubectl logs <pod-name> -c <container>`        | Get container logs from multi-container pod  | `kubectl logs webapp -c auth-service`           |
| `kubectl exec -it <pod-name> -- <command>`      | Execute command in pod                       | `kubectl exec -it nginx-pod -- /bin/bash`       |
| `kubectl port-forward <pod-name> <local-port>:<pod-port>` | Forward pod port to local            | `kubectl port-forward nginx-pod 8080:80`        |

## Deployment Operations

| Command                                           | Description                        | Example                                         |
|---------------------------------------------------|------------------------------------|-------------------------------------------------|
| `kubectl get deployments`                         | List all deployments               | `kubectl get deploy`                            |
| `kubectl describe deployment <name>`              | Show deployment details            | `kubectl describe deploy nginx-deploy`          |
| `kubectl create deployment <name> --image=<image>`| Create a deployment                | `kubectl create deploy nginx --image=nginx`     |
| `kubectl scale deployment <name> --replicas=<count>` | Scale a deployment              | `kubectl scale deploy nginx --replicas=5`       |
| `kubectl rollout status deployment <name>`        | Check rollout status               | `kubectl rollout status deploy nginx`           |
| `kubectl rollout history deployment <name>`       | View rollout history               | `kubectl rollout history deploy nginx`          |
| `kubectl rollout undo deployment <name>`          | Rollback deployment                | `kubectl rollout undo deploy nginx`             |
| `kubectl rollout restart deployment <name>`       | Restart deployment (for image refresh) | `kubectl rollout restart deploy nginx`      |
| `kubectl set image deployment/<name> <container>=<image>` | Update container image        | `kubectl set image deployment/nginx nginx=nginx:latest` |
| `kubectl delete deployment <name>`                | Delete a deployment                | `kubectl delete deploy nginx`                   |

## Service Operations

| Command                               | Description           | Example                         |
|---------------------------------------|-----------------------|---------------------------------|
| `kubectl get services`                | List all services     | `kubectl get svc`               |
| `kubectl describe service <name>`     | Show service details  | `kubectl describe svc nginx-svc`|
| `kubectl expose deployment <name> --type=<type> --port=<port>` | Expose a deployment as a service | `kubectl expose deploy nginx --type=NodePort --port=80` |
| `kubectl delete service <name>`       | Delete a service      | `kubectl delete svc nginx-svc`  |

## ConfigMap and Secret Operations

| Command                                                   | Description                          | Example                                         |
|-----------------------------------------------------------|--------------------------------------|-------------------------------------------------|
| `kubectl create configmap <name> --from-literal=<key>=<value>` | Create a ConfigMap from literal value | `kubectl create configmap app-config --from-literal=env=prod` |
| `kubectl create configmap <name> --from-file=<path>`      | Create a ConfigMap from file         | `kubectl create configmap app-config --from-file=config.properties` |
| `kubectl get configmaps`                                  | List all ConfigMaps                  | `kubectl get configmaps`                        |
| `kubectl describe configmap <name>`                       | Show ConfigMap details               | `kubectl describe configmap app-config`         |
| `kubectl delete configmap <name>`                         | Delete a ConfigMap                   | `kubectl delete configmap app-config`           |
| `kubectl create secret generic <name> --from-literal=<key>=<value>` | Create a Secret from literal value | `kub
::contentReference[oaicite:0]{index=0}
 
## Persistent Volume Operations

| Command | Description |
|--------|-------------|
| `kubectl get persistentvolumes` | List PVs |
| `kubectl get persistentvolumeclaims` | List PVCs |
| `kubectl describe persistentvolumeclaim <name>` | Show PVC details |

## Tips

| Tip | Description |
|-----|-------------|
| `kubectl explain <resource>` | Show API docs for a resource |
| Add `-o yaml` or `-o json` | Get output in specific format |
| Use aliases like `alias k=kubectl` | Speed up CLI usage |