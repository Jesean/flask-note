### hash哈希操作

* ### 添加

```
语法:
hset key field value

示例:
# 设置person键并定义person下的字段为field，字段对应的值为angle
hset person name angle
```

* #### 获取哈希中的field对应的值

```
语法:
hget key field

示例:
# 获取person下的字段的值
127.0.0.1:6379> hget person name
"angle"
```

* #### 删除field中的某个field

```
语法:
hdel key field[field...]

示例:
hdel person name
```

* #### 获取某个哈希中所有的field和value

```
语法:
hkeys key

示例:
127.0.0.1:6379> hset person name angle
(integer) 1
127.0.0.1:6379> hset person age 18
(integer) 1
127.0.0.1:6379> hset person sex boy
(integer) 1

# 获取person下的所有的字段
127.0.0.1:6379> hkeys person
1) "name"
2) "age"
3) "sex"
```

* #### 获取某个哈希中所有的值



