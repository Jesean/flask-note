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
  * 使用expires参数

  * ```
    one:
    expires = datetime(year=2018,month=7,day=14,hour=16,minute=29,second=0)

    two:
    # 使用expires参数，就必须使用格林尼治时间
    # 要相对北京时间少8个小时
    expires = datetime(year=2018, month=7, day=14, hour=8, minute=29, second=0)

    three:
    # 设置距离多久
    expires = datetime.now() + timedelta(seconds=1) - timedelta(hours=8)

    resp.set_cookie("name", "value", expires=expires)
    ```

* 设置cookie的有效域名



