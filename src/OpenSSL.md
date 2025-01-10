# OpenSSL

## Print info

```
openssl x509 -in file.pem.crt -text -noout
```

## Self CA setup

Generate CA cert and key
```
openssl req -new -x509 -days <duration> -extensions v3_ca -keyout ca.key -out ca.crt
```

## Key generation

Generate private (server or client) RSA key that is encrypted with AES256
```
openssl genrsa -aes256 -out server.key 2048
```
> server.key

Generate private (server or client) RSA key without encryption
```
openssl genrsa -out server.key 2048
```
> server.key

Generate a certificate signing request to send to the CA.
```
openssl req -out server.csr -key server.key -new
```
> server.csr

## Signing certificate signing request (.csr)
.csr file can be sent to CA and it will return certificate (public key)

We can also sign that .csr request with our own CA key but it won't be trusted by 3rd party software (like browser)
```
openssl x509 -req -in server.csr -CA ca.crt -CAkey ca.key -CAcreateserial -out server.crt -days <duration>
```


