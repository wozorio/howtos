# Create basic deploymets on AKS

> **NOTE**: this procedure describes how to run a simple apache pod on AKS

1. Log on to Azure through AzureCLI on PowerShell\
`az login`

1. Set the subscription you want to work with\
`az account set --subscription <subscription_name>`

1. Get credentials of the AKS cluster you want to work with\
`az aks get-credentials --resource-group <rg_name> --name <aks_cluster_name> --admin`

1. Access the dashboard of your Kubernetes cluster\
`kubectl proxy`

1. Enter the following URL on the internet browser\
`http://localhost:8001/api/v1/namespaces/kube-system/services/kubernetes-dashboard/proxy/#!/overview?namespace=default`

1. See which VMs (Worker Nodes) are composing up the Kubernetes cluster\
`kubectl get nodes`

1. Create a new namespace\
`kubectl create ns foo`

1. Run your app under your namespace\
`kubectl run apache --namespace default --image=httpd --replicas=1 --port=80 --labels="app=apache"`

1. Create a service to expose the containers and load-balance user requests\
`kubectl expose --namespace default deployment apache --name apache-svc --port=80 --target-port=80 --type=LoadBalancer`

1. Alternatively, you can also create a YAML file with the desired config and apply it using the syntax below:\

**apache-service.yaml**
```yaml
apiVersion: v1
kind: Service
metadata:
  name: apache-service
  annotations:
    service.beta.kubernetes.io/azure-load-balancer-internal: "true"
  labels:
    app: apache
spec:
  type: LoadBalancer
  loadBalancerIP: "10.240.0.100"
  ports:
  - port: 80
    protocol: TCP
    name: http
  selector:
    app: apache
```

`kubectl create -f .\apache-service.yaml --namespace foo`
