# Creating self-signed certificates

Useful to serve within your server.

### Generate a private key:
`openssl genpkey -algorithm RSA -out server.key`

### Generate a certificate signing request (CSR):
`openssl req -new -key server.key -out server.csr`

### Generate the self-signed certificate:
`openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt`

Dummy files are placed in this directory just to serve as an example.