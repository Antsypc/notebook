Client Error
======

> [rfc7231 - HTTP code 4xx](https://tools.ietf.org/html/rfc7231#section-6.5)

## 400 Bad Request
服务端拒绝处理客户端发起的请求,可能是由于,请求格式不正确等.

## 402 Payment Required
保留中.

## 403 Forbidden
客户端请求没有进行认证,可能是由于密码不正确,证书不正确等.当然,有时未认证就请求一个资源,可能返回 404,就当做对这个用户而言根本不存在这个资源.

## 404 Not Found
服务端找不到对应的资源时,返回 404.状态默认被缓存.

## 405 Method Not Allowed
请求方式不被服务器接受,比如使用 `GET` 访问一个只允许 `POST` 的资源.状态默认被缓存.

## 406 Not Acceptable
客户端在请求资源时,会指定自己期望返回的数据格式,当服务端发现自身不能返回相应格式时,返回 406.

## 408 Request Timeout
服务端接受了一半数据,然后剩下的迟迟不来,超时了,就返回 408 并关闭连接.

## 409 Conflict
由于和被请求的资源的当前状态之间存在冲突，请求无法完成。冲突通常发生于对 PUT 请求的处理中。例如，在采用版本检查的环境下，某次 PUT 提交的对特定资源的修改请求所附带的版本信息与之前的某个（第三方）请求向冲突.

## 410 Gone
资源永久不存在了.

## 411 Length Required
服务端拒绝请求是由于 request header 没有 Content-Length 域.

## 413 Payload Too Large
请求体数据太长.

## 414 URI Too Long
请求的URI太长了,所以被服务端拒绝.这种情况可能是 POST 转 GET 请求导致的,攻击啊什么的.

## 415 Unsupported Media Type
请求体数据格式不被服务端接受, payload unformat.比如Content-Type or Content-Encoding 以及内容本身的格式等有问题.

## 417 Expectation Failed
The 417 (Expectation Failed) status code indicates that the
expectation given in the request's Expect header field
(Section 5.1.1) could not be met by at least one of the inbound
servers.

> [解释及解决办法](http://blog.csdn.net/ni_hao_ya/article/details/8162118)
 
## 426 Upgrade Required
服务端强制要求客户端采用更高版本的协议,并相应 426 头信息.例如:
 
    HTTP/1.1 426 Upgrade Required
    Upgrade: HTTP/3.0
    Connection: Upgrade
    Content-Length: 53
    Content-Type: text/plain
    
