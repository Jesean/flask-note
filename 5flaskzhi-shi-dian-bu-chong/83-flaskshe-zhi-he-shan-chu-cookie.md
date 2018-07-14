### flask操作cookie

* 设置cookie：设置cookie在Response对象上进行设置的，通过"flask.Response"对象上的一个"set\_cookie\(\)"方法来进行设置cookie信息

```
# response对象
resp = Response("name")
# 设置cookie值
resp.set_cookie("name","value")
```

* 删除cookie：通过"flask.Response"对象上的一个"delete\_cookie\(\)"方法来进行设置cookie信息

```
# 删除指定cookie
resp.delete_cookie("name")
```

* 设置cookie的有效期
  * 使用max\_age参数设置有效期事件
    * ```
      # max_age:距离多少秒后cookie值过期
      resp.set_cookie("name","value",max_age=10)
      ```
* 设置cookie的有效域名



