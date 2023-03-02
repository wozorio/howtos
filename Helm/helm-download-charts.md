# Helm - Download a particular chart locally with Helm 2.X

1. Initialize helm locally (without Tiller)
    ```bash
    helm init --client-only
    ```
1. List all available versions of a particular chart
    ```bash
    helm search repo -l stable/nginx-ingress
    ```
1. Download the desired chart version
    ```bash
    helm fetch stable/nginx-ingress --version 1.22.1 --untar
    ```
