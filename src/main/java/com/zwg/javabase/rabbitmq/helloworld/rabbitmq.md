# rabbitmq

#### rabbitmq 介绍
1. rabbitmq  是一个使用elang语言编写的高性能的消息中间件,消息队列一般有两种传递模式:点对点(P2P,Point to-Point)模式,和发布/订阅(Pub/Sub)模式.点对点是基于队列的,生产者将消息发送到队列,消费者从队列中接受消息.发布订阅模式定义了如何向一个内容节点发布和订阅消息,这个内容节点一般称为topic(主题),消息发布者将消息发送到某个主题,而消息订阅者则从主题中订阅消息.
 2. 消息中间件的作用: 解耦,缓冲,异步通信


#### rabbitmq模型

 1. 整体架构

    1.1 生产者将消息(通常json格式)序列化以后,发送到交换机(exchange),同时会携带routingkey

    1.2 exchange将消息发送到与它通过routingkey绑定的队列中,一个exchange可以绑定多个队列,如果生产者发送携带的routngKey能够与队列与交换机绑定的routingKey进行匹配,则会把消息投递到相匹配的队列中,如果没有匹配,则会通知生产者或者直接丢弃.exchange本身并不会存储消息,消息是存放在队列中的

 2. 相关参数介绍

    2.1 队列:队列是存放消息的对象,消费者可以从队列中获取消息,多个消费者可以订阅同一个队列,队列中的消息是采用轮询的方法分别投递给各个消费者的.

    2.2 exchange(交换机),交换机为rabbirmq处理消息的中转站,生产者会把消息发送到交换机中,然后再由交换机将消息发送到一个或多个队列中,如果没有匹配的队列,则交换机会把消息返回或者直接丢弃.

    交换机有4种模式:1.fault模式,交换机会将消息发送到所有与该交换机绑定的队列中 2.direct ,





  2.32

 1.生产者和消费者



