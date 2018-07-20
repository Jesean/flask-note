befor\_first\_request:处理第一次请求之前执行

before\_request:在每次请求之前执行。通常可以用这个装饰器来给视图函数增加一些变量

teardown\_appcontext:不管是否有异常，注册的函数都会在每次请求之后执行

template\_filter:在jinja2模板的时候自定义过滤器，比如可以增加一个upper的过滤器

context\_processor:上下处理器。返回的字典中的键可以在模板上下文中使用

errorhandler:errorhandler接收状态码，可以自定义返回这种状态码的响应的处理方法



