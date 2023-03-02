# Azure - Azure CLI - Login (Service Principal)

1. Login
    ```bash
    az login
    ```
1. List all subscriptions
    ```bash
    az account list
    ```
1. Set a specific subscription to work with
    ```bash
    az account set -s <subscription_name> or <subscription_id>
    ```
1. Refresh access token in case it expires
    ```bash
    az account get-access-token
    ```
