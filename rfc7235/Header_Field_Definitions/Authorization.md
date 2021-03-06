“Authorization”头字段允许用户代理去与源服务器认证它自己，通常不是必须的，在接收到一个401响应后。它的值由包含用户代理认证信息的对被请求资源的域的凭证组成。

> ```
>      Authorization = credentials
> ```

如果一个请求是被认证的并且域被指明，那么相同的凭证被假定为对所有其他在这个域上的请求都是有效的（假定认证方案自身没有要求，就像凭证随质询的值变化或使用同步时钟。）

转发请求的代理**不得**修改那个请求中的任何Authorization字段。查看RFC7234的3.2节了解有关HTTP缓存处理Authorization字段的更多细节和要求。