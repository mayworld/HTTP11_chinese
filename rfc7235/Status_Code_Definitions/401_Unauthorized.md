401装填吗表明请求没有被应用，应为它缺少对那个目标资源的有效的认证凭证。生成401响应的服务器**必须**发送WW-Authenticate头字段，其包含至少一个适用于那个目标资源的质询。

如果请求包含认证凭证，那么401响应表明那么凭证的认证已经被拒绝。用户代理**可以**使用一个新的或者替换Authorization头字段（4.2节）进行重试。如果401响应包含了于先前响应相同的质询，并且用户代理已经试图认证过至少一次，那么用户代理**应该**给用户呈现封闭表示，因为它通常包含了相应的诊断信息。