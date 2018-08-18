### 1.相关链接

celery:[http://docs.celeryproject.org/en/latest/getting-started/first-steps-with-celery.html](http://docs.celeryproject.org/en/latest/getting-started/first-steps-with-celery.html)

### 2.关系

![](/assets/190-1.png)

### 3.安装&准备

* redis
* 安装celery

```
pip install celery
```

* 在Windows操作系统上，还需要安装另外一个东西,eventlet

```
pip install eventlet
```

redis:[http://docs.celeryproject.org/en/latest/getting-started/brokers/redis.html\#broker-redis](http://docs.celeryproject.org/en/latest/getting-started/brokers/redis.html#broker-redis)

安装

```
pip install -U "celery[redis]"
```

配置

```
app.conf.broker_url = 'redis://localhost:6379/0'
-------------------------------------------------
redis://:password@hostname:port/db_number
```



