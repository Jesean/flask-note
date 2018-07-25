## python操作redis

1.安装

```
pip install redis
```

2.新建一个文件redis\_demo.py，然后初始化一个redis实例变量，并且在Ubuntu虚拟机找那个开启redis

```
# 从redis包中导入Redis类
from redis import Redis
# 初始化redis实例变量
op_redis = Redis(host="192.168.5.128",port=6379)
```

3.对字符串的操作:操作redis的方法名称，跟之前使用redis-cli一样

```
# 1.字符串
# 设置
op_redis.set("name","angle")
# 获取数据
name = op_redis.get("name")
print(name)
# 删除
op_redis.delete(name)


# 2.列表的操作
# 添加
op_redis.lpush("languages","java")
op_redis.lpush("languages","python")
op_redis.lpush("languages","c/c++")
# 获取集合中的所有元素
print(op_redis.lrange("languages",0,-1))


# 3.集合的操作
# 添加
op_redis.sadd("like","a")
op_redis.sadd("like","b")
op_redis.sadd("like","c")
# 获取集合中的所有元素
like = op_redis.smembers('like')
print(like)


# 4.哈希的操作
# 添加web键，和几个字段以及对应的值
op_redis.hset('web','baidu','www.baidu.com')
op_redis.hset('web','python','www.python.com')
op_redis.hset('web','google','www.google.com')
# 获取所有的字段及其值
web = op_redis.hgetall('web')
print(web)
```



