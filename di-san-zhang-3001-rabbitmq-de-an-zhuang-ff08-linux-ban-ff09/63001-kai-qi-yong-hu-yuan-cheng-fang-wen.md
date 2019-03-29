默认情况下，RabbitMQ的默认的guest用户只允许本机访问， 如果想让guest用户能够远程访问的话，只需要将配置文件中的loopback_users列表置为空即可，如下：
```bash
{loopback_users, []}
```
另外关于新添加的用户，直接就可以从远程访问的，如果想让新添加的用户只能本地访问，可以将用户名添加到上面的列表, 如只允许admin用户本机访问。
```bash
{loopback_users, ["admin"]}
```
更新配置后，别忘了重启服务哦！

```bash
sudo /sbin/service rabbitmq-server status  # 查看服务状态
```

![](/_book/assets/1553757137819.png)



这里可以看到log文件的位置，转到文件位置，打开文件：

![](/_book/assets/1553757148332.png)


这里显示的是没有找到配置文件，我们可以自己创建这个文件

```bash
cd /etc/rabbitmq/
vi rabbitmq.config
```

编辑内容如下：

```bash
[{rabbit, [{loopback_users, []}]}].
```

这里的意思是开放使用，rabbitmq默认创建的用户guest，密码也是guest，这个用户默认只能是本机访问，localhost或者127.0.0.1，从外部访问需要添加上面的配置。

保存配置后重启服务：

```bash
service rabbitmq-server stop
service rabbitmq-server start
```

此时就可以从外部访问了，但此时再看log文件，发现内容还是原来的，还是显示没有找到配置文件，可以手动删除这个文件再重启服务，不过这不影响使用

```bash
rm rabbit\@mythsky.log 
service rabbitmq-server stop
service rabbitmq-server start
```

注意:记得要开放5672和15672端口

```bash
/sbin/iptables -I INPUT -p tcp --dport 5672 -j ACCEPT
/sbin/iptables -I INPUT -p tcp --dport 15672 -j ACCEPT
```

本文参考：[传送门](https://blog.csdn.net/qq_22075041/article/details/78855708)