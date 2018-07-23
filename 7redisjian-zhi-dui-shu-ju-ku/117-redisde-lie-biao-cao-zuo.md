### 列表操作

* #### 在列表左边添加元素

```
语法:lpush key values

示例:lpush name angle
lpush name angle miku
```

将值value插入到列表key的表头。如果key不存在，一个空列表会被创建并执行lpush操作。当key存在但不是列表类型时，将返回一个错误。

* #### 在列表右边添加元素

```
语法: rpush key values

示例: rpush websites www.qq.com 0 -1
```

将值value插入到列表可以的表尾。如果可以不存在，一个空列表会被创建并执行RPUSH操作。当key存在但不是列表类型时，返回一个错误。

* ### 查看列表中的元素

```
语法:lrange key start stop

示例:lrange name 0 1
```

返回列表key中指定区间内的元素，区间以偏移量start和stop指定如果要左边的第一个到最后的一个lrange key 0 -1

* ### 移除列表中的元素

  * 移除并返回列表key的头元素

  ```
  lpop key
  ```

  * 移除并返回列表的尾元素

  ```
  rpop key
  ```

  * 移除并返回列表可以的中间元素

  ```
  lrem key couont value
  ```

将删除可以key这个列表中，count个值为value的元素

