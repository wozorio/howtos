# Kubernetes - Delete Evicted pods from all namespaces

```bash
kubectl get pods --all-namespaces | grep Evicted | awk '{print $2 " --namespace=" $1}' | xargs -n 2 -d '\n' bash -c 'kubectl delete pod $0 $1'
```
