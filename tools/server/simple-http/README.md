# Simple HTTP Server

Easy to deploy http server for various of reasons.

## Using docker

Here are some commands to quickly deploy http server.

### Step #1
First, go to `tools\helper\create-cert` to create self signed certificate to host pages under https.

### Step #2

Rename example file to conf file under `conf-available` directory.

Append following lines to hosts file in your system:
```
# /etc/hosts # Linux
# C:\Windows\System32\drivers\etc\hosts # Windows

127.0.0.1 localhost
127.0.0.1 page.test
```

### Step #3

Next, copy server.crt and server.key to certs directory, and run the following command.

```
# In windows we use backtick `, in linux we use backslash \ for multi line commands
docker run -dit `
  --name apache `
  -v .\httpd.conf:/usr/local/apache2/conf/httpd.conf `
  -v .\certs\server.crt:/usr/local/apache2/conf/server.crt `
  -v .\certs\server.key:/usr/local/apache2/conf/server.key `
  -v .\conf-available:/etc/apache2/conf-available/ `
  -v .\public-html:/usr/local/apache2/htdocs/ `
  -p 80:80 -p 443:443 `
  httpd:2.4
```

### Step #4

Test if the pages are working served with https using these URLs:

- https://localhost/
- https://page.test/index.html

The certs are self-signed, unless you signed the certs with trusted CA the browser will warn you about it.

Done!

#### Helper commands

Open interactive shell inside apache container:
`docker exec -it apache /bin/bash`