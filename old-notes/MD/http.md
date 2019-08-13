http是基于Tcp/ip协议的应用程序协议，规定客服端和服务器之间的通信格式
Content-Type：服务器回应时，告诉客户端数据是什么格式
Content-Encoding: 数据压缩
缺点：
    http/1.0 tcp连接的新建成本很高 -- connection:keep-alive
HTTP/1.1
    1.引入持久连接（客户端的最后一个请求时，发送connenction:close）
    2.管道机制：在同一个TCP请求中，客户端可以同时发送多个请求
    3.content-length 区分数据包，前提：声明本次回应的数据长度（不使用）
    4.分块传输编码：Transfer-Encoding表明将由数量未定的数据块组成
    缺点：
        在同一个TCP连接里，所有数据通信是按次序进行，（队头堵塞）
        --减少请求数，同时多开持久连接
HTTP2
    复用TCP连接，在一个连接里，客户端和浏览器都可以同时发送多个请求或回应，而且不用按照顺序一一对应，这样就避免了"队头堵塞"
    多工：双向的，实时的通信
    数据流：每个请求或回应的所有数据包（客户端可以指定数据流的优先级）
    ID:奇客户，偶服务
    头信息压缩机制：header compression(头信息使用gzip或compress压缩发送；客户端和服务器同时维护同一张头信息表，发送索引号)
    服务器推送