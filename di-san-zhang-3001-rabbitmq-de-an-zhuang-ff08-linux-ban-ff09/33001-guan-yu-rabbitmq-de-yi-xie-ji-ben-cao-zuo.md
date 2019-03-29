```bash

$ sudo chkconfig rabbitmq-server on  # 添加开机启动RabbitMQ服务
$ sudo /sbin/service rabbitmq-server start # 启动服务
$ sudo /sbin/service rabbitmq-server status  # 查看服务状态
$ sudo /sbin/service rabbitmq-server stop   # 停止服务
 
# 查看当前所有用户
$ sudo rabbitmqctl list_users
 
# 查看默认guest用户的权限
$ sudo rabbitmqctl list_user_permissions guest
 
# 由于RabbitMQ默认的账号用户名和密码都是guest。为了安全起见, 先删掉默认用户
$ sudo rabbitmqctl delete_user guest
 
# 添加新用户
$ sudo rabbitmqctl add_user username password
 
# 设置用户tag
$ sudo rabbitmqctl set_user_tags username administrator
 
# 赋予用户默认vhost的全部操作权限
$ sudo rabbitmqctl set_permissions -p / username ".*" ".*" ".*"
 
# 查看用户的权限
$ sudo rabbitmqctl list_user_permissions username
```

更多关于rabbitmqctl的使用，可以参考[帮助手册](https://www.rabbitmq.com/rabbitmqctl.8.html)。