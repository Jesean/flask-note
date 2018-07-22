### telnet操作memcached:

##### telnet登录memcached

```
telnet ip地址 端口号
telnet 127.0.0.1 11211
```

注意:memcached存储数据是以键值对的方式存储的

1.添加数据:

* set\(设置\):

  * 语法:

  ```
  set key 0(否)(是否压缩) timeout(过期时间) value_length(字符串的长度)
  value
  ```

  * 示例:

  ```
  set username 0 60 7
  abcdefg
  ```

* add\(添加\):

  * 语法:

  ```
  add key 0(否)(是否压缩) timeout value_length
  value
  ```

  * 示例:

  ```
  add username 0 60 7
  abcdefg
  ```

  set 和 add 的区别:add是只负责添加数据，不会去修改数据。如果添加的数据的key已经存在了，则添加失败，如果是添加的key不存在，则添加成功。而set不同，如果memcached中不存在相同的key，则进行添加，如果存在，则替换。

2.获取数据

* 语法:

```
get key
```

* 示例:

```
get username
```

3.删除数据

* 语法:

```
delete key
```

* 示例:

```
delete username
```

* flush\_all:删除memcached中的所有键值对。

4.查看memcached的当前状态

* 语法:stats

```
'get_hists':get命令命中了多少次
'get_misses':get命令get空了几次
'curr_items':当前'memcached'中的键值对的个数
```

5.增加

```
set age 0 120 2     > 20
incr age 2          > 22
注意:必须都是数值类型，不然会报错
```

6.减少

```
decr age 2          > 20
```



