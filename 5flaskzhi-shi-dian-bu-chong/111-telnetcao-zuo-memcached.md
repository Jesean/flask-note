### telnet操作memcached:

连接到别的机器的memcached

```
telnet ip地址 11211
telnet 127.0.0.1 11211
```

1.添加数据:

* set:

  * 语法:

  ```
  set key flas(是否压缩) timeout value_length
  value
  ```

  * 示例:

  ```
  set username 0 60 7
  abcdefg
  ```

* add:

  * 语法:

  ```
  add key flas(0) timeout value_length
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

* flush\_all:删除memcached中的所有数据。

4.查看memcached的当前状态

* 语法:stats



