### flask操作cookie

* 设置cookie：设置cookie在Response对象上进行设置的

```
# response对象
resp = Response("name")
# 设置cookie值
resp.set_cookie("name","value")
```

* 删除cookie

```
# 删除指定cookie
resp.delete_cookie("name")
```

* 设置cookie的有效期
* 设置cookie的有效域名



