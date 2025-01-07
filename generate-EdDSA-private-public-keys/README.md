# Generate EdDSA private/public keys

## Generate Ed25519 private key

```sh
openssl genpkey -algorithm ed25519 -out private.pem
```

## Generate Ed448 private key

```sh
openssl genpkey -algorithm ed448 -out private.pem
```

#### Sample

```sh
-----BEGIN PRIVATE KEY-----
…
-----END PRIVATE KEY-----
```

## Generate public key from private key

```sh
openssl pkey -in private.pem -pubout -out public.pem
```

#### Sample

```sh
-----BEGIN PUBLIC KEY-----
…
-----END PUBLIC KEY-----
```

## References

- [RFC8032 Edwards-Curve Digital Signature Algorithm (EdDSA)](https://datatracker.ietf.org/doc/html/rfc8032)
- [Wikipedia: EdDSA](https://en.wikipedia.org/wiki/EdDSA)
