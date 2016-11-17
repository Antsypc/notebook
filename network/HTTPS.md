HTTPS
=====


#### Nginx服务器配置HTTPS
[Nginx HTTPS Configuration](http://nginx.org/en/docs/http/configuring_https_servers.html)

创建服务器私钥
> openssl genrsa -des3 -out server.key 2048

签名请求的证书
> openssl req -new -key server.key -out server.csr

制作解密后的私钥
> openssl rsa -in server.key -out server_nopwd.key      
> openssl x509 -req -days 3650 -in server.csr -signkey server_nopwd.key -out server.crt

拷贝证书文件
> cp /usr/local/nginx/server.crt /usr/local/nginx/html/

nginx 配置文件
```
server {
    listen              443 ssl;
    server_name         www.example.com;
    ssl_certificate     www.example.com.crt;
    ssl_certificate_key www.example.com.key;
    ssl_protocols       TLSv1 TLSv1.1 TLSv1.2;
    ssl_ciphers         HIGH:!aNULL:!MD5;
    ...
}
```
