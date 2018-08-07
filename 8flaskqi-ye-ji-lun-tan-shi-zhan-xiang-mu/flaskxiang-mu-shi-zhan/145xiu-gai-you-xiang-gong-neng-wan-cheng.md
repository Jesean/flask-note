### 1.在生成验证码的时候存入memcached中

自定义memcached的set、get、delete操作，便于后期修改

```
import memcache

# debug=True，如果出现错误，会打印出来
cache = memcache.Client(["127.0.0.1:11211"],debug=True)

# 设置
def set(key,value,timeout=60):
    return cache.set(key,value,timeout)

# 获取
def get(key):
    return cache.get(key)

# 删除
def delete(key):
    return cache.delete(key)
```



