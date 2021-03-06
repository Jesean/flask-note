# 10 必会的小细节知识

## 让其他电脑访问我的网站

如果想在同一个局域网下的其他电脑访问自己的电脑上的Flask网站

那么可以设置'host="0.0.0.0"'才能访问得到

## 指定端口号

Flask项目，默认使用'5000'端口，如果想要更换端口，那么可以设置'port=9000'

## url唯一

在定义url的时候，一定要记住在最后加一个斜杠

1.如果不加斜杠，那么在浏览器中访问这个url的时候，如果最后加了斜杠，那么就访问不到，这样用户体验不太好

2.搜索引擎会将不加斜杠的和加斜杠的示为两个不同的url，而其实加和不加斜杠的都是同一个url，那么就会搜索引擎造成一个误解，加了斜杠，就不会出现没有斜杠的情况

## 'GET'请求和'POST'请求

'GET'在网络请求中有许多请求方式，比如'GET'，'POST'，DELETE,PUT请求等，那么最常用的就是'GET'和'POST'请求

1.'GET'请求:只会在服务上获取资源，不会更改服务器的状态。这种请求方式推荐使用'GET'请求

2.'POST'请求：会给服务器提交一些数据或者文件，一般POST请求是会对服务器的状态产生影响,那么这种请求推荐使用post请求

3.关于参数传递:

'GET'请求:把参数放到'url'中，通过'?xx=xxx'的形式传递，因为会把参数放到url中，这样会不很安全

'POST'请求:把参数放到'Form Data'中，会把参数放到Form Data中，避免了被偷瞄的风险。可以通过抓包的形式进行分析，因为POST请求可以提交一些数据给服务器，比如可以发送文件，那么就增加了很大的风险。所以POST请求，对于那些有经验的黑客来讲，其实是更不安全

4.在'Flask'中,'route'方法，默认将只能使用'GET'的方式请求这个url，如果想要设置自己的请求方式，那么应该传递一个'POST'请求

