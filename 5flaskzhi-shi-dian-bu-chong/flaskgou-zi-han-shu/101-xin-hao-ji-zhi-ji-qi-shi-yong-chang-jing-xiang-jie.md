#### 安装

```
pip install blinker
```

#### 自定义信号:自定义信号分三步，第一是定义一个信号，第二是监听一个信号，第三是发送一个信号。

* 定义信号:定义信号需要使用到blinker这个包的Namespace类来创建一个命名空间。比如定义一个在访问了某个视图函数的时候的信号。示例代码如下:

```
from blinker import Namespace

mysignal = Namespace()
visit_signal = mysignal.signal('visit-signal')
```

* 监听信号:监听信号使用singel对象的connect方法，在这个方法中需要传递一个函数，用来接收以后监听到这个信号该做的事情。示例代码如下:

```
def visit_func(sender,username):
    print(sender,username)
```

* 发送信号:发送信号使用singal对象的send方法，这个方法可以传递一些其他参数过去。示例代码如下:

```
mysignal.send(username='angle')
```



