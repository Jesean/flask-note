## 关于响应

视图函数的返回值会被自动转换一个响应对象，flask的转换逻辑如下:

* 如果返回的是一个合法的响应对象，则直接返回
* 如果返回的是一个字符串，那么flask会重新创建一个werkzeug.wrappers.Response对象，Response将给字符串作为主体，状态码是200，MIME类型为text/html,然后返回该Response对象
* 如果返回的是一个元组，元组中的数据类型是\(response.status.headers\)。status值会覆盖默认的200状态码，headers可以是一个列表或者字典，作为额外的消息头
* 如果以上条件都不满足，Flask会假设返回值是一个合法的wsgi应用程序

---

### 自定义响应

自定义响应必须满足三个条件:

* 必须继承自Response类
* 必须实现类方法force\_type\(cls,rv,environ=None\)
* 必须制定app.response\_clss为自定义的Response



