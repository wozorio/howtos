# OpenSSL - Extract private key and public cert from PFX

1. Extract the private key
    ```
    CERT_NAME="my_certificate_name"

    openssl pkcs12 -in ${CERT_NAME}.pfx -passin pass: -nodes -nocerts -out ${CERT_NAME}.key
    ```
1. Extract the public certificate
    ```
    openssl pkcs12 -in ${CERT_NAME}.pfx -passin pass: -clcerts -nokeys -out ${CERT_NAME}.crt
    ```
1. Extract the CA certificates (root and intermediates)
    ```
    openssl pkcs12 -in ${CERT_NAME}.pfx -passin pass: -cacerts -chain -nokeys -out ${CERT_NAME}-ca.crt
    ```
1. Combine the public certificate and the CA certificates together in a single file (fullchain)
    ```
    cat ${CERT_NAME}.crt ${CERT_NAME}-ca.crt > ${CERT_NAME}-fullchain.crt
    ```
