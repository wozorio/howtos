# Azure - AKS - Connect with SSH to Azure Kubernetes Service (AKS) cluster nodes for maintenance or troubleshooting

1. Run a debian container image and attach a terminal session to it. This container can be used to create an SSH session with any node in the AKS cluster
    
    ```bash
    kubectl run -it --rm aks-ssh --image=debian
    ```

1. Once the terminal session is connected to the container, install an SSH client using apt-get

    ```bash
    apt-get update && apt-get install openssh-client -y
    ```

1. Open a new terminal window, not connected to your container, list the pods on your AKS cluster using the kubectl get pods command. The pod created in the previous step starts with the name aks-ssh, as shown in the following example

    ```bash
    $ kubectl get pods
    NAME                       READY     STATUS    RESTARTS   AGE
    aks-ssh-554b746bcf-kbwvf   1/1       Running   0          1m
    ```

1. Now copy your private SSH key into the helper pod. This private key is used to SSH into the AKS node

1. Provide your own aks-ssh pod name obtained in the previous step. If needed, change ~/.ssh/id_rsa to location of your private SSH key

    ```bash
    kubectl cp id_rsa aks-ssh-554b746bcf-kbwvf:/id_rsa
    ```

1. Return to the terminal session to your container, update the permissions on the copied id_rsa private SSH key so that it is user read-only
    ```bash
    chmod 0600 id_rsa
    ```
1. Create an SSH connection to your AKS node. Again, the default username for AKS nodes is azureuser. Accept the prompt to continue with the connection as the SSH key is first trusted. You are then provided with the bash prompt of your AKS node

    ```bash
    $ ssh -i id_rsa azureuser@10.240.0.4
    ```
