### 参数解析：

Flask-Restful插件提供了类似wtForms来验证提交的数据是否合法的包，叫做reqparse。

基本用法:

```
parser = reqparse.RequestParser()
parser.add_argument('username',type=str,help='请输入用户名',required=True)
args = parser.parse_args()
```

add\_argument可以指定这个字段的名字，这个字段的数据类型等。

参数详细讲解:

1. default:默认值，如果这个参数没有值，那么将使用这个参数指定的值
2. required:是否必须，如果这个参数没有值，那么将使用这个参数指定的值
3. type:这个参数的数据类型，如果指定，那么将使用指定的数据类型来强制转换提交上来
4. choices:选项。提交上来的值只有满足这个选项中的值才符合验证通过，否则验证不通过
5. help:错误信息。如果验证失败后，将会使用这个参数指定的值作为错误信息
6. trim:是否要取出前后的空格

其中的type，可以使用python自带的一些数据类型，也可以使用flask\_restful.inputs下的一些特定的数据累心来强制转换。

常用的:

1. url:会判断这个参数的值是否是一个url，如果不是，就会抛出异常
2. regex:正则表达式
3. date:将这个字符串转换为datetime.date。如果转换不成功，则会抛出一个异常



