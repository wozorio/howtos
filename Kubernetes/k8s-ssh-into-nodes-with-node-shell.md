# Kubernetes - SSH into worker nodes with node-shell

1. Install Krew https://krew.sigs.k8s.io/docs/user-guide/setup/install/

1. Add the repo for node-shell
   ```
   kubectl krew index add kvaps https://github.com/kvaps/krew-index
   ```
1. Install node-shell
   ```
   kubectl krew install kvaps/node-shell
   ```
1. SSH into the desired worker node
   ```
   kubectl node-shell <worker_node>
   ```
