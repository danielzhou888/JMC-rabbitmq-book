如果只从命令行操作RabbitMQ，多少有点不方便。幸好RabbitMQ自带了web管理界面，只需要启动插件便可以使用。

```bash
$ sudo rabbitmq-plugins enable rabbitmq_management
```

然后通过浏览器访问

http://10.100.1.46:15672

输入用户名和密码访问web管理界面了。

![](/_book/assets/1553772014172.png)