这次修改的主要变化是编辑性的:提取消息传递语法并将HTTP语义划分为核心功能，条件请求，部分请求，缓存和身份验证的单独文档。一致性语言已经被修改以明确地针对需求，并且已经改进术语以将有效载荷与资源的表示和表示区分开来。

一个新的要求已经被添加，当这些语义与请求方法不一致时，嵌入到URI中的语义被禁用，因为这是互操作性失败的常见原因。(第2节)

已经添加了用于确定有效载荷是否与特定标识符相关联的算法。 （第3.1.4.1节）

文本媒体类型的默认字符集ISO-8859-1已被删除; 现在默认是无论媒体类型定义如何。 同样，ISO-8859-1的特殊处理已从Accept-Charset标题字段中删除。 （第3.1.1.3节和第5.3.3节）

Content-Location的定义已经改变，不再影响解析相对URI引用的基本URI，这是由于实现支持不佳以及潜在地破坏内容协商资源中的相对链接的不良效果。 （第3.1.4.2节）

为了与[RFC7230]的方法中立的解析算法一致，GET的定义已经放宽，因此请求可以具有主体，即使主体对GET没有意义。 （第4.3.1节）

服务器不再需要处理所有Content- *头字段，并且在PUT请求中明确禁止使用Content-Range。 （第4.3.4节）

CONNECT方法的定义已经从[RFC2817]转移到了这个规范。 （第4.3.6节）

OPTIONS和TRACE请求方法已被定义为安全的。 （第4.3.7节和第4.3.8节）

Expect标题字段的扩展机制由于广泛部署的中断实现而被删除。 （第5.1.1节）

Max-Forwards标题字段已被限制在OPTIONS和TRACE方法中; 以前，扩展方法也可以使用它。 （第5.1.2节）

当没有引用URI可用时，“about：blank”URI已经被建议作为Referer头域的值，这与其他引用域没有被发送或被删除的情况区分开来。 （5.5.2节）

下面的状态码现在是可缓存的（也就是说，它们可以被缓存存储和重新使用，而没有明确的新鲜度信息存在）：204,404,405,414,501。（第6节）

201（已创建）状态说明已更改为允许创建多个资源的可能性。 （第6.3.2节）

203（非权威信息）的定义已经扩大到包括有效载荷转换的情况。 （6.3.4节）

可自动重定向的安全请求方法不再关闭;用户代理能够基于请求方法语义进行确定。重定向状态码301,302和307不再对响应有效载荷和用户交互有规范要求。 （6.4节）

状态码301和302已被更改为允许用户代理重写方法从POST到GET。 （6.4.2和6.4.3节）

对303（见其他）状态代码的描述已经被改变，以便在给出明确的新鲜度信息时对其进行高速缓存，并且对GET的303响应添加了特定的定义。 （6.4.4节）

由于有关代理的带内配置的安全问题，305（使用代理）状态代码已被弃用。 （第6.4.5节）

400（错误请求）状态代码已被放宽，因此不限于语法错误。 （6.5.1节）

426（需要升级）状态代码已经从[RFC2817]中引入。 （6.5.15节）

HTTP日期和Date标题字段的要求目标已经减少到那些生成日期的系统，而不是所有的系统发送日期。 （第7.1.1节）

Location头域的语法已经被改变，以允许所有的URI引用，包括相对引用和片段，以及关于何时使用片段不合适的一些澄清。 （第7.1.2节）

Allow已被重新分类为响应头字段，删除选项以在PUT请求中指定它。允许的相关要求已经放宽;相应地，客户不需要总是相信它的价值。 （第7.4.1节）

方法注册表已被定义。 （第8.1节）

状态码注册表已被本规范重新定义;以前，它是在[RFC2817]的7.1节中定义的。 （第8.2节）

内容编码的注册已经改变，要求IETF评估。 （8.4节）

由于现在由[RFC6266]定义，所以Content-Disposition头部字段已被删除。

Content-MD5头字段已被删除，因为它与部分响应不一致。