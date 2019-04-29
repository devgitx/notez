# FullStack Plan 2017

首先假定需求是全端的，app web 甚至加上桌面客户端，那么需要：



1. app 分为android和ios两大平台，可以考虑使用react native，代码基本可以复用。

2. web前端 html css加上js，如上可以考虑用react完整技术栈，也可以用vue等其它类库。还需要一个或多个charts开源图表类库绘制前端图表。

3. 桌面客户端 使用electron。一次开发支持linux win macos三大平台，大部分代码可以和web前端复用，本地存储使用sqlite。

4. web后端 可选择的很多，python php java go ruby nodejs都可选，c c++就不要考虑了，不是不行，做web项目太累。后端提供rest风格的api就可以，所有的客户端调用同一套api。一般特定的开源框架说法，也是指向这一层，推荐一些个人最偏爱的，php - lumen，python - flask，java - spring，node - koa，go - denco，ruby当然是rails。。。

1. 数据库    10万客户端加实时行情量级并不是很大，就不建议马上上分库分表，高可用大集群之类的方案了。优先选择云端实例模式，比如阿里云的RDS。自己搭建的话，一主二从做好同步和读写分离，再加个延时冷备的库，基本够用。可选mysql或postgresql，mysql技术层面接受度会高很多。

6. 缓存 推荐使用redis，完全当缓存用，不要考虑持久化存储。初期随意混用会加大架构复杂度。redis也有云端实例直接购买使用，自己搭建可以搞个2 3个点的小集群，也够用了。

7. 队列 这里才是题设中的zeromq用武之地，但是我们有更好的选择。考虑稳定性，持久化，更多特性的，可以选用rabbitmq，完胜zeromq。考虑极致性能的，选用kafka。

8. 代理层 lvs集群接下所有网络请求再分发，选用云端产品的话不用考虑。

9. web服务器 nginx最佳选择，考虑openresty改版，很多全局逻辑，如限流等，可以在这层写lua脚本实现，简单强大。nginx配置反向代理，直接指向web后端提供的服务端口，web后端服务器上可以跑多进程，占用多个端口实现。

10. 跨服session 复用上面的redis缓存，session存储在缓存中。

11. 连接层 dns和域名，找个靠谱的域名商购买加备案，dns可以购买dnspod服务。链路最好全部https，需要花钱买证书，或者使用let's encrypt的免费证书。

1. 连接方式    实时行情实时性要求高，就推荐长连接的方式了，最佳选择websocket。轮询的方式也可以。

2. 服务器    直接购买选用云环境的全套吧，加上带宽。这个规模下，自建的成本优势还体现不出来，直接使用全套云基础设施，时间和资金成本都节约很多。阿里云，腾讯云，或者其它云商都可以考虑，实际测试比对之后选择。

14. cdn 既然是实时行情，cdn作用不大，但是为了分担静态资源请求压力和加快访问，可以考虑买个七牛的cdn服务。

==== 可选 ====

1. 存储    开始估计还用不上，如果有大量历史数据需要存储，可以考虑搭建一套。可选方案也很多，ceph，weedfs，hdfs，首选hdfs。

16. 监控等周边配套 很多团队初期会不考虑，可以视情况购买些服务。

1. 安全    扯开又是大话题了，初期基本也不会多加考虑，数据保证接近实时备份吧

18. 搜索 开始也用不上吧？如果需要，要搭建一套搜索索引集群，可选solr和es，推荐es。

19. 其它 如果开始web后端选型选的是java，可能还要一些中间件，数据库访问，rpc服务治理用的dubbo等，视情况使用。 如果要保证各个集群高可用性，还需要选择zookeeper或者keepalive之类的方案。 如果业务上有使用需求，可以购买邮件群发，短信群发，app推送，支付接入等服务，都有专业的公司提供。

做完这些，产品才算可用了！
