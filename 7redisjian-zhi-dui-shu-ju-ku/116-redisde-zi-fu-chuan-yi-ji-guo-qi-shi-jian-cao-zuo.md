### 连接redis

```
redis-cli -h 127.0.0.1 -p 6379 或者redis-cli
```

### 设置key-velue

语法:

```
set key value
```

示例:

```
set name angle
```

### 获取value

语法:

```
get key
```

示例:

```
get name
```

注意:如果设置值为多个单词，需要添加双引号

```
127.0.0.1:6379> set username "hello world"
OK
127.0.0.1:6379> get username
"hello world"
```



