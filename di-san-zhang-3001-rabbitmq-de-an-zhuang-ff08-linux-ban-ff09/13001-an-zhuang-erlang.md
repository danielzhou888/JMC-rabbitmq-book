由于RabbitMQ依赖Erlang， 所以需要先安装Erlang。

Erlang的安装方式大概有两种：

    1. 从Erlang Solution安装(推荐)
```bash
# 添加erlang solutions源
$ wget http://www.rabbitmq.com/releases/erlang/erlang-19.0-1.el7.centos.x86_64.rpm
$ sudo rpm -Uvh erlang-19.0-1.el7.centos.x86_64.rpm
$ sudo yum install erlang
```

    2. 从EPEL源安装(这种方式安装的Erlang版本可能不是最新的，有时候不能满足RabbitMQ需要的最低版本)
```bash
# 启动EPEL源
$ sudo yum install epel-release 
# 安装erlang
$ sudo yum install erlang  
```