### 通过python操作memcached

#### 1.安装

```
pip install python-memcached
```

#### 2.建立连接

```
mc = memcache.Client(["127.0.0.1:11211"],debug=True)
```

#### 3.设置数据

```
mc.set(key="name",val="angle",time=60,min_compress_len=5)

# 设置多个值
mc.set_multi({'title':r'小红帽','content':r'没有内容'},time=100)
```

#### 4.获取数据

```
mc.get('title')
```

#### 5.删除数据

```
mc.delete('name')
```

#### 6.自增长

```
# 默认自增加一,delta属性设置增加值
mc.incr('age',delta=10)
```

#### 7.自减少

```
mc.decr('age',delta=10)
```



