### How Python uses SSL Certificate :

Python uses certifcate in two ways :
- (1) By using `certifi` module
- (2) By using System CA Store 

#### First Validate if certifcaite is correct -
- (1) Download the certificate 
```
openssl s_client -showcerts -connect <Host>:<Port> < /dev/null 2> /dev/null | openssl x509 -outform PEM > /tmp/My_Application.pem
```
(2) Check the certificate validity by below commands. It should give status-code 200 -
```
/usr/bin/python
>>> import requests
>>> r = requests.get('https://<Host>:<Port>', verify="/tmp/My_Application.pem")
>>> r.status_code
200
```
---

#### By using `certifi` module:
- (1) Check what is the path of `cacert.pem` file by below commands -
```
import certifi
print(certifi.where())
```
- (2) open /tmp/My_Application.pem. Copy from top "-----BEGIN CERTIFICATE-----" to "-----END CERTIFICATE-----"
- (3) open `cacert.pem` in vi mode and append certificate at end of file and save.
---

#### System CA Store (if certifi not used)

- **Linux:**  usually _/etc/ssl/certs/ca-certificates.crt_ or _/etc/pki/tls/certs/ca-bundle.crt_ or run below command on RHEL with `root` :
```
cp My_Application.pem /etc/pki/ca-trust/source/anchors/My_Application.crt
``` 
Copies the certificate to the anchors directory, which is where RHEL expects custom trusted CA certificates.
```
sudo update-ca-trust extract:
```
Processes all CA certificates in the source/anchors directory and reconstructs the system’s CA trust bundle
- **macOS:** system Keychain or /private/etc/ssl/cert.pem
- **Windows:** Windows Certificate Store (but requests doesn’t directly use it unless patched; instead it uses certifi).
---
