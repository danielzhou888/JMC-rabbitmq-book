该服务将使用其默认设置正常运行。你可以自定义RabbitMQ环境或编辑配置。 
（1）erl环境变量配置
```bash
ERLANG_HOME=C:\Program Files\erl9.2
```

![](/assets/1553601059048.png)

在Path中加入

```bash
 %ERLANG_HOME%\bin;
```
![](/assets/1553601084040.png)

测试erl配置是否正确，开始-运行-cmd，输入erl，显示如下，证明配置正确 

![](/assets/1553601097801.png)


（2）RabbitMQ环境变量配置
这里注意，看好你RabbitMQ的安装位置，以及安装的版本，我的版本为3.7.3

```bash
RABBITMQ_SERVER=C:\Program Files\RabbitMQ Server\rabbitmq_server-3.7.3
```

![](/assets/1553601121620.png)

在Path中加入

```bash
%RABBITMQ_SERVER%\sbin;
```
![](/assets/1553601140918.png)
