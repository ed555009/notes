# SSL Conversion

This is a simple script to convert a SSL certificate from one format to another.

## Extracting certificate & key from a PFX file

### Extract private key

```sh
openssl pkcs12 -in ssl.pfx -nocerts -out private.key
```

### Extract certificate

```sh
openssl pkcs12 -in ssl.pfx -clcerts -nokeys -out ssl.crt
```

## Convert PFX to PEM

```sh
openssl pkcs12 -in ssl.pfx -nodes -out ssl.pem
```

## Remove passphrase from private key

```sh
openssl rsa -in private.key -out decrypted_private.key
```
