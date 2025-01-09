# openssl-encrypt-decrypt-file

## generate keypair

```
openssl genrsa -out server.pem
```

## extract public key

```
openssl rsa -in server.pem -pubout > server.pub
```

## encrypt file using public key

```
openssl pkeyutl -encrypt -inkey server.pub -pubin -in rahasia.txt -out rahasia.enc
```

### Base64 version

```
openssl pkeyutl -encrypt -inkey server.pub -pubin -in rahasia.txt | base64 > rahasia.enc
```

## decrypt file using private key

```
openssl pkeyutl -decrypt -inkey server.pem -in rahasia.enc
```

### BASE64 version

```
base64 -d rahasia.enc | openssl pkeyutl -decrypt -inkey server.pem
```
