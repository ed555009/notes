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
