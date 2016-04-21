Server Error
=======

> [Server Error - HTTP code 5xx](https://tools.ietf.org/html/rfc7231#section-6.6)

## 500 Internal Server Error
服务器内部执行发生错误.

## 501 Not Implemented
客户端请求的方式服务端不支持,如不支持 PUT 请求 balabala,可能是由于服务器版本过低,客户端使用了错误的请求方式.

## 502 Bad Gateway
IP 的网关写错了,导致不能转接,或者使用的代理或网关不同意交换数据,协议不正确之类的.

## 503 Service Unavailable
服务端由于过载,一时无法立即相应请求,可能相应 503,并给出延迟多久再次请求.但是,实际实现时往往直接拒绝连接请求.

## 504 Gateway Timeout
客户端通过网关或代理获取相应超时.

## 505 HTTP Version Not Supported
HTTP 版本对应协议服务器不支持,有时是真的版本太低,但有时可能是请求头写错了,比如 `GET` 后只能有一个空格.
