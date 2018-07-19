```
class LoginForm(Form):
    # # 验证邮箱
    # email = StringField(validators=[Email()])
    # # 验证用户是否输入
    # username = StringField(validators=[input_required()])
    # # 验证范围
    # age = IntegerField(validators=[NumberRange(12,18)])
    # # 正则表达式
    # phone = StringField(validators=[Regexp(r'1[34578]\d{9}')])
    # # url验证
    # home_page = StringField(validators=[URL()])
    # # uuid值验证
    # uuid = StringField(validators=[UUID()])
    # 1234
    captcha = StringField(validators=[Length(4,4)])

    # 自定义验证器
    # valiedate_name
    def validate_captcha(self,field):
        # print(type(field))
        # 字段数据值
        # print(field.data)
        if field.data != "1234":
            raise ValidationError("验证码错误")
```



