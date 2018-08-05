验证更改密码的表单

```
class ResetpwdForm(BaseForm):
    oldpwd = StringField(validators=[Length(6,20,message="请输入正确格式的密码")])
    newpwd = StringField(validators=[Length(6,20,message="请输入正确格式的密码")])
    newpwd2 = StringField(validators=[EqualTo("newpwd")])

```



