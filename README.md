# How to connect to localhost with a self signed certificate

This one pops ina while, and despite being quite easy to do. This howto will generate the certificate and install it on your iOS simulators.

# Create a Self-Signed SSL Certificate

`openssl genrsa -aes256 -passout pass:x -out server.pass.key 2048`

`openssl rsa -passin pass:x -in server.pass.key -out server.key`

`rm server.pass.key`

`openssl req -new -sha256 -key server.key -out server.csr -subj /CN=localhost`

`openssl x509 -req -sha512 -days 365 -in server.csr -signkey server.key -out server.crt`



# Import the certificate

Clone https://github.com/ADVTOOLS/ADVTrustStore.git
run it: ./iosCertTrustManager.py -a server.crt
