### flask内置9种信号

* template\_rendered:模板渲染完毕后的信号

```
def template_rendered_func(sender,template,context):
        print("sender:{}".format(sender))
        print("template:{}".format(template))
        print("context:{}".format(context))
template_rendered.connect(template_rendered_func)
```

* request\_started:模板开始渲染
* request\_finished:模板完成渲染
* got\_request.exception:在请求过程中抛出异常时发送，异常本身会通过exception传递到订阅的函数
* request\_tearing\_down:request对象被销毁的信号
* got\_request\_exception:视图函数发生异常的信号，一般可以监听这个信号，来记录网站异常信号
* appcontext\_tearing\_down:app上下文被销毁的信号
* appcontext\_pushed:app上下文被推入到栈上的信号
* appcontext\_poped:app上下文被退出栈中的信号
* message\_flashed:调用了Flask的‘flashed’方法的信号



