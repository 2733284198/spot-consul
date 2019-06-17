# spot-consul
基于consul的，在aws竞价实例、弹性伸缩组环境下，自适应负载均衡实现方案。

# 背景
当前的负载均衡有以下几大卖点：
1. 权重自适应学习
2. 在线策略控制
3. 客户端Nginx权重选择算法

但存在几个问题，相对于服务端学习控制讲：
1. 学习放在客户端，每种语言客户端实现就得重新实现一遍
2. 容易引起客户端的共振，且共振的解决不如服务端控制力强
3. 客户端复杂带来一些锁和开销
4. 负载均衡的算法升级需要客户端升级，而客户端集成到业务系统里，业务系统还需要升级，这是不太现实的

# 目标
* 实现服务端权重控制
* 重写consul客户端，c++/golang版本

# 设计草图
![spot-consul-design](assets/spot-consul-design-v1.JPG)

