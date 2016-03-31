Redirection 3xx
===============
> [rfc7231 - HTTP code 3xx](https://tools.ietf.org/html/rfc7231#section-6.4)

重定向分为以下四种情况:
- 请求的资源已移动到另一个URI. 301 (Moved Permanently), 302 (Found), and 307(Temporary Redirect).
- 请求的资源有很多被选项,可以从合适的一个资源中获取. 300 (Multiple Choices) status code.
- 服务器端已处理重定向到另一个资源. 303 (See Other) status code.
- 资源被缓存了,直接从cache中获取. 304 (Not Modified) status code.

## 300 Multiple Choices
该资源有多个 URI,现在需要客户端选择一个进行请求.如果服务端有比较好的建议,就把 URI 放在 Location 域.

## 301 Moved Permanently
请求的资源已经永久不存在了,如果服务端有比较好的建议,就把 URI 放在 Location 域.
由于历史实现原因,某些客户端可能再次请求时将 POST 改为 GET,如果不希望客户端的这个操作,可以返回307状态码.

## 302 Found
请求的资源临时改到另一个 URI.服务器返回头中应把对应的 URI 写在 Location 域.
由于历史实现原因,某些客户端可能再次请求时将 POST 改为 GET,如果不希望客户端的这个操作,可以返回307状态码.

## 303 See Other
服务器端已经对请求的资源重定向到另一个 URI,并把其值写在了 Location 域.或者服务器建议客户端重新对该 URI 进行请求.

## 304 Not Modified
本次请求的资源和上次请求的没有变化,可以直接从缓存中获取.

## 305 Use Proxy
deprecated!

## 306 (Unused)
目前未被使用,保留中.

## 307 Temporary Redirect
资源临时改为另外的 URI,服务端将其写在了相应头的 Location 域.但是!该响应码表示不能改变请求方式!这是与302不同的一点.
