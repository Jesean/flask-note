### 常用的验证器

数据发过来时，经过表单验证，因此需要验证器来进行验证，以下对一些常用的内置验证器进行讲解:

* Email:验证上传的数据是否为邮箱

```
# 验证邮箱
email = StringField(validators=[Email()])
```

* EqualTo:验证上传的数据是否和另外一个字段相等，常用的就是密码和确认密码两个字段是否相等

```
# EqualTo指定与之保持相同值的字段
password_repeat = StringField(validators=[Length(min=6,max=10),EqualTo("password")])
```

* InputRequired:原始数据的需要验证。如果不是特殊情况，应该使用InputRequired。

```
# 验证用户是否输入
username = StringField(validators=[input_required()])
```

* Length:长度限制，有min和max两个值进行限制

```
username = StringField(validators=[Length(min=3,max=10,message="用户名长度必须在3到10位之间")])
```

* NumberRange:数字的区间，有min和max两个值限制，如果处在两个数字之间则满足

```
# 验证范围
age = IntegerField(validators=[NumberRange(12,18)])
```

* Regexp:自定义正则表达式

```
# 正则表达式
phone = StringField(validators=[Regexp(r'1[34578]\d{9}')])
```

* URL:必须要是URL的形式

```
# url验证
home_page = StringField(validators=[URL()])
```

* UUID:验证UUID

```
# uuid值验证
uuid = StringField(validators=[UUID()])
```

---



