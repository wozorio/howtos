# Azure - ACR - Query images via command-line

1. Define variables
    ```bash
    ACR_NAME="acr_name"
    REPO="repo_name"
    IMAGE_TAG="image_tag"
    IMAGE_DIGEST="sha256:a86a34b162534c1fd1ec13ad078b87402512c2a4afe0cae3175b0a1aa39e8146"
    ```

1. Query image by tag
    ```bash
    az acr repository show -n "${ACR_NAME}" --image "${REPO}:${IMAGE_TAG}"
    ```
1. Query image by manifest digest
    ```bash
    az acr repository show -n "${ACR_NAME}" --image "${REPO}@${IMAGE_DIGEST}"
    ```
