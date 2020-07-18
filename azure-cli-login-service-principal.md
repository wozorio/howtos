# Azure - Azure CLI - Login (Service Principal)

1. Login with a Service Principal

    ```azcli
    az login --service-principal -u <service_principal_id> -p <password> --tenant <tenant_id>
    ```

1. List all subscriptions

    ```azcli
    az account list
    ```

1. Set a specific subscription to work with

    ```azcli
    az account set -s <subscription_name> or <subscription_id>
    ```

1. Refresh access token in case it expires

    ```azcli
    az account get-access-token
    ```
