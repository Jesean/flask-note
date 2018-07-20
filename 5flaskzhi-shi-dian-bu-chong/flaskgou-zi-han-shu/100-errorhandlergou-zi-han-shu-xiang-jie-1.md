errorhandler:errorhandler接收状态码，可以自定义返回这种状态码的响应的处理方法

```
@app.errorhandler(500)
def serror_error(error):
return "服务器刷新的太频繁"

@app.errorhandler(404)
def not_found(error):
return "not found"
```



