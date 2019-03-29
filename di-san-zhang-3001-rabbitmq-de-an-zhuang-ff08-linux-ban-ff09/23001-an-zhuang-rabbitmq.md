先下载rpm：
```bash
wget http://www.rabbitmq.com/releases/rabbitmq-server/v3.6.15/rabbitmq-server-3.6.15-1.el7.noarch.rpm
```

下载完成后安装：
```bash
yum install rabbitmq-server-3.6.15-1.el7.noarch.rpm
```

安装时如果遇到下面的依赖错误
```java
Error: Package: socat-1.7.2.3-1.el6.x86_64 (epel)
       Requires: libreadline.so.5()(64bit)
```

可以尝试先执行
```java
sudo yum install socat
```