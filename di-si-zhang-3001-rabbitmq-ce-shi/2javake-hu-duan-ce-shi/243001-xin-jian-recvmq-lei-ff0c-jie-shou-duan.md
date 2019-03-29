```java
package com.scmd.rabbitmq;

import com.rabbitmq.client.*;

import java.io.IOException;
import java.util.concurrent.TimeoutException;

/**
 * @program: scmd-knb-common
 * @description: 消费者
 * @author: zhouzhixiang
 * @create: 2019-03-28 20:07
 */
public class ReceiveRabbitMQ {

    private final static String QUEUE_NAME = "Hello";

    public static void main(String[] args) throws IOException, TimeoutException {
        ConnectionFactory factory = new ConnectionFactory();
        factory.setHost("10.100.1.46");
        factory.setPort(5672);
        factory.setUsername("zhouzhixiang");
        factory.setPassword("zhouzhixiang");
        Connection connection = factory.newConnection();
        Channel channel = connection.createChannel();
        channel.queueDeclare(QUEUE_NAME, false, false, false, null);
        System.out.println(" [x] Wait for messages. To exit press CTRL + C");
        Consumer consumer = new DefaultConsumer(channel) {
            @Override
            public void handleDelivery(String consumerTag, Envelope envelope, AMQP.BasicProperties properties, byte[] body) throws IOException {
                String message = new String(body, "UTF-8");
                System.out.println(" [x] Received '" + message + "'");
            }
        };
        channel.basicConsume(QUEUE_NAME, true, consumer);
    }
}

```

发送与接收后的状态图：

![Alt text](./1553775301273.png)
![Alt text](./1553775313762.png)
![Alt text](./1553775324018.png)
![Alt text](./1553775338179.png)



本文参考：[传送门](https://blog.csdn.net/qq_31634461/article/details/79377256)