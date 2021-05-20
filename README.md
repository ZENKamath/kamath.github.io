kamath.github.io
================

### JSON to code 
1. https://quicktype.io/
2. https://netheril96.github.io/autojsoncxx/

### Openssl
https://eclipsesource.com/blogs/2016/09/07/tutorial-code-signing-and-verification-with-openssl/

#### 1. Create pem file
```bash
openssl rsa -in ~/.ssh/id_rsa -pubout -out skamath.pem
```

#### 2. Signing a blob
```bash
openssl dgst -sha256 -sign ~/.ssh/id_rsa -out sign.sha256 ./curl-7_55_0.tar.gz
openssl enc -base64 -in sign.sha256 -out sign.base64
```

#### 2. Verifying a blog
```bash
openssl enc -base64 -d -in sign.base64 -out sign_out.sha256 
openssl dgst -sha256 -verify skamath.pem -signature sign_out.sha256 ./curl-7_55_0.tar.gz
```
