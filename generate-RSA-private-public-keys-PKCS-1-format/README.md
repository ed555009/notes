# Generate RSA private/public keys in PKCS#1

## Generate private key

```sh
openssl genrsa -out private.key 2048
```

#### Sample

```sh
-----BEGIN RSA PRIVATE KEY-----
…
-----END RSA PRIVATE KEY-----
```

#### Convert PKCS#8 to PKCS#1

If the generated private key is in PKCS#8 format, convert it to PKCS#1 format using the following command:

```sh
openssl rsa -in private_pkcs8.pem -out private_pkcs1.pem -traditional
```

## Generate public key from private key

```sh
openssl rsa -in private.key -out public.pem -RSAPublicKey_out
```

#### Sample

```sh
-----BEGIN RSA PUBLIC KEY-----
…
-----END RSA PUBLIC KEY-----
```
