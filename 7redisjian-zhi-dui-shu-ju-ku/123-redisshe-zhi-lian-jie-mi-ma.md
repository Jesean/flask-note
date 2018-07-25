### 设置redis密码

在windows中，配置文件为redis.windows-service.conf

在Ubuntu中，配置文件为redis.conf

将配置文件中的"requirepass password"

```
redis-cli -h 127.0.0.1 -p 6379 -a 123456
```



