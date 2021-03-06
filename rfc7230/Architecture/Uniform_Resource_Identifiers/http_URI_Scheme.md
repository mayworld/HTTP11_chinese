这里定义“http”URI方案是为了通过他们与分层命名空间的关联来标识标识符，该分层命名空间由潜在HTTP源服务商监听给定端口的TCP（[RFC0793]）连接管理。

> ```
>   http-URI = "http:" "//" authority path-abempty [ "?" query ] [ "#" fragment ]
> ```

“http”URI的源服务器由权威(authority)组件标识，其中包含主机标识符和可选的TCP端口（[RFC3986]，3.2.2节）。分级路径(path)组件和可选的查询(query)组件作为一个源服务器的命名空间内的目标资源的识别码进行服务。可选的片段（fragment）组件允许间接识别辅助资源，不依赖URI方案，在RFC3986的3.5节中定义。

一个发送者**不得**产生一个空主机识别码的“http”URI。接收者处理这样的一个URI引用必须视为无效而拒绝它。

如果主机识别码是作为IP地址提供的，源服务器在那个IP地址上指定的TCP端口的监听者（如果有的话）。如果主机是一个注册的名字，那么注册名字是与名称解析服务（例如DNS）一起使用的间接标识符，用于查找该源服务器的地址。如果端口子组件没有给出或者为空，默认是TCP80端口（为WWW服务保留的端口）。

注意到带有一个权威组件的URI存在并不意味着始终存在一个HTTP服务监听在那个主机和端口上。任何人都可以创造一条URI。权威组件决定的是谁有权利来权威的响应指向确定资源的请求。已注册名称和IP地址的委派属性创造了一个联合命名空间，这基于对指定端口和主机的控制而不论HTTP服务是否存在。查看9.1节来了解关于建立权威的安全注意事项。

当在一个上下文中使用一个“http”URI来访问给定资源的时候，客户端可能尝试将主机解析为一个IP地址，建立一个到那个地址的给定端口的TCP连接，然后发送一个包含URI的识别数据（第5节）HTTP请求消息（第三节）到那个服务器来访问。如果服务器用一个非临时的HTTP响应消息（在RFC7231第6节中描述）来应答这个请求，那么响应被视为对客户端请求的权威应答。

虽然HTTP是独立于传输协议的，但“http”方案特定于基于TCP服务，因为名称委托进程依靠TCP建立权威。基于一些其他底层连接协议的HTTP服务可能会使用不同的URI方案进行标识，就像“https”方案用于需要端到端安全连接的资源。其他协议也可以用来提供对“http”标识的资源的访问 - 它只是TCP特有的权威接口。

权限的URI通用语法还包括用于在URI中包含一个弃用了的用于用户认证信息的用户信息子组件（[RFC 3986]，第3.2.1节）。一些实现使用用户信息组件来对认证信息进行内部配置，例如在命令调用选项，配置文件或书签列表中，尽管这样的使用可能暴露用户标识符或密码。当一个“http”URI引用在一条消息中作为请求目标或者头字段的值被产生，发送者**不得**产生用户信息子组件（和它的“@”标识符）。在使用从不可信源接收到的“http”URI参考之前，接收者应该解析用户信息并将它的存在作为错误处理。它很可能为用来了钓鱼攻击而掩盖权威。
