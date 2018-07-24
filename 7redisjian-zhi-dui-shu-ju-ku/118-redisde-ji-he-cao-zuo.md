### set集合的 操作

* #### 添加元素

```
语法:
sadd key member[member...]

示例:
# 向a集合中添加1、2、3、4、5、6
sadd a 1 2 3 4 5 6
```

* #### 查看元素

```
语法:
smembers key

示例:
# 查看a集合中元素
smembers a
```

* #### 移除元素

```
语法:
srem key members[members...]

示例:
# 从a集合中移除1、2元素
srem a 1 2
```

* #### 查看集合中的元素个数

```
语法:
scard a

示例:
# 查看a集合有几个元素
scard a
```

* #### 获取多个集合的交集

```
语法:
sinter key[key...]

示例:
# 返回a、b集合的交集
sinter a b
```



