# webdav server

apache2 based webdav server running on docker.

### Setup

Create the base docker image.

`docker build -t apache-dav .`

Files and directories are already created for test purposes. You can just run following command.

```
# In windows we use backtick `, in linux we use backslash \ for multi line commands
docker run -dit `
  --name apache-dav `
  -v .\httpd.conf:/usr/local/apache2/conf/httpd.conf `
  -v .\certs\server.crt:/usr/local/apache2/conf/server.crt `
  -v .\certs\server.key:/usr/local/apache2/conf/server.key `
  -v .\webdav:/usr/local/apache2/conf/extra/webdav/ `
  -p 8080:80 -p 4443:443 `
  apache-dav
```

After server starts, following endpoints should be available to use:
```
hostname/test # Digest access authentication example
hostname/test-basic # Basic access authentication example
```

You can duplicate directories under `webdav` or edit current ones to customize your endpoints.
