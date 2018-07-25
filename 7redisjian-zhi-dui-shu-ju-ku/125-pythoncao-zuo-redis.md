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



