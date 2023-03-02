# Kubernetes Cheat Sheet

1. Get cluster information
    ```bash
    kubectl cluster-info
    ```
1. SSH into a running pod in interactive mode
    ```bash
    kubectl attach -it <pod_name> -c <container_name>
    ```
1. Run a command on a running container and exit it. `netstat` is being used just as an example
    ```bash
    kubectl exec -it <pod> -- netstat
    ```
1. Check which clusters you have cached credentials (stored in kubeconfig file)
    ```bash
    kubectl config get-contexts
    ```
1. Switch connection to another cluster that already has cached credentials
    ```bash
    kubectl config use-context <context_name>
    ```
1. Access the Kubernetes dashboard
    ```bash
    kubectl proxy
    ```
1. On the computer where `kubectl proxy` was executed, open up a browser and enter the appropriate address  
**K8s 1.15 and below**: `http://127.0.0.1:8001/api/v1/namespaces/kube-system/services/kubernetes-dashboard:/proxy`  
**K8s 1.16 or greater**: `http://127.0.0.1:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy`

1. Port forward a deployment to the client machine
    ```bash
    kubectl port-forward deployment/<deployment_name> <client_machine_port>:<pod_port>
    ```
1. Show all logs from a pod
    ```bash
    kubectl logs <pod_name>
    ```
1. Show all logs from a pod generated over the last hour
    ```bash
    kubectl logs --since=1h <pod_name>
    ```
1. Show only the most recent 20 lines from a pod
    ```bash
    kubectl logs --tail=20 <pod_name>
    ```
1. Show logs from a specific app
    ```bash
    kubectl logs --ignore-errors=true --max-log-requests=50 -f -l app=<app_name>
    ```
