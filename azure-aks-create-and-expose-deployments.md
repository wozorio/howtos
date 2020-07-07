# Azure - AKS - Create and expose deployments

1. Create a new namespace\
`kubectl create ns foo`

1. Create a deployment manifest with the desired config
    ```yaml
    apiVersion: apps/v1
    kind: Deployment
    metadata:
      labels:
        app: apache
      name: apache
    spec:
      replicas: 2
      selector:
        matchLabels:
          app: apache
      strategy:
        rollingUpdate:
          maxSurge: 1
          maxUnavailable: 1
        type: RollingUpdate
      template:
        metadata:
          labels:
            app: apache
        spec:
          containers:
            - name: apache
              image: httpd:2.4
              ports:
                - containerPort: 80
    ```
1. Alternatively the deployment can also be created with kubectl run\
`kubectl run apache --namespace foo --image=httpd --replicas=2 --port=8080 --labels="app=apache"`

1. Create a service to expose the deployment and load-balance user requests\
`kubectl expose --namespace foo deployment apache --name apache-svc --port=80 --target-port=8080 --type=LoadBalancer`

1. Create a service manifest with the desired config
    ```yaml
    apiVersion: v1
    kind: Service
    metadata:
      name: apache
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
 1. Apply it using the syntax below\
`kubectl create -f apache-service.yaml --namespace foo`

1. Alternatively the deployment can also be exposed with kubectl expose\
`kubectl expose --namespace foo deployment apache --name apache-svc --port=80 --target-port=8080 --type=LoadBalancer`
