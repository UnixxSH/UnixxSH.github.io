### convert crt/key to pks on Windows
```
openssl pkcs12 –export –out certificate.pfx –inkey rsaprivate.key –in certificate.crt –certfile fileca.crt
```