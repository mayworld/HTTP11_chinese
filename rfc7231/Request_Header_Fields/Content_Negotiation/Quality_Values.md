主动协商的很多请求头字段使用命名为“q“（不区分大小写）的通用参数来给关联内容的种类的优先级分配一个权重。这个权重被称为”质量价值“（或”q值“）应为相同的名称经常被用于服务器配置来给资源可能被选择的各种表示的相对质量分配一个权重。

权重被归一化为0到1的实数，其中0.001时最低优先级而1时最高优先级；0表示不可接受。如果没有”q“参数出现，默认权重是1.

> ```
>      weight = OWS ";" OWS "q=" qvalue
>      qvalue = ( "0" [ "." 0*3DIGIT ] )
>             / ( "1" [ "." 0*3("0") ] )
> ```

q值的发送者**不得**生成小数点后超过三个数字的数。这些值的用户配置应该被限制为相同的形式。