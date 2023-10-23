# Install a root CA certificate in the trust store

> **NOTE:** It is important to have the .crt extension on the file, otherwise it will not be processed.

1. Create the `/usr/local/share/ca-certificates` directory if it does not exist

   ```bash
   sudo mkdir -p /usr/local/share/ca-certificates
   ```

1. Install `ca-certificates`

   ```bash
   sudo apt install -y ca-certificates
   ```

1. Copy the root CA certificate to the `ca-certificates` directory

   ```bash
   sudo cp {{ file_name }}.crt /usr/local/share/ca-certificates
   ```

1. Update `ca-certificates`

   ```bash
   sudo update-ca-certificates
   ```
