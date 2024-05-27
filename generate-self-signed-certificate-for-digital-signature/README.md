# Generate self-signed certificate for digital signature

This is for e-Signature like DocuSign, DocuSeal, etc. usage.

## Generate private key & certificate

```sh
openssl req -x509 -newkey rsa:4096 -sha256 -nodes -keyout signing-key.pem -out signing-cert.pem -days 36500 -addext "keyUsage = digitalSignature, nonRepudiation, keyEncipherment"
```

## Confirm certificate is eligible for digital signature

Check the `Key Usage` field in the certificate, it should contains `Digital Signature` and `Non Repudiation`.

```sh
openssl x509 -in signing-cert.pem -text -noout
```

## Convert to PKCS#12 format (PFX)

```sh
openssl pkcs12 -export -in signing-cert.pem -inkey signing-key.pem -out signing.pfx
```
