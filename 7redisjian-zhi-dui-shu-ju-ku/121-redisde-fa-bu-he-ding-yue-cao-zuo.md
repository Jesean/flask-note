## 发布/订阅操作

* ### 给某个频道发布消息

```
语法:
publish channel message

示例:
127.0.0.1:6379> publish channe2 hello
(integer) 1
127.0.0.1:6379>

```

* ### 订阅某个频道的消息

```
语法:
subscribe channel[channel...]


```



