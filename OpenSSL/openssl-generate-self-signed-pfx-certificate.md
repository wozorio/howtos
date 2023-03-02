# OpenSSL - Generate a self-signed certificate (PFX)

1. Create a new RSA key and public certificate
    ```
    openssl req -newkey rsa:2048 -nodes -keyout token_signing.key -x509 -days 365 -out token_signing.pem -subj "//O=My Coporation Name\ST=My Corporation state\C=BR"
    ```
1. Create a PFX certificate using the RSA key and public certificate from the previous step
    ```
    winpty openssl pkcs12 -inkey token_signing.key -in token_signing.pem -export -out token_signing.pfx
    ```
