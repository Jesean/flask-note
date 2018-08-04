### cms登录post请求

```
    def post(self):
        # 验证表单
        form = LoginForm(request.form)
        if form.validate():
            email = form.email.data
            password = form.password.data
            remember = form.remember.data
            user = CMSUser.query.filter_by(email=email).first()
            if user and user.check_password(password):
                session['user_id'] = user.id
                if remember:
                    # 持久化
                    # 如果设置session.parmanet=True，那么过期时间是31天
                    session.permanent = True
                # 反转蓝图规则:蓝图名.视图
                return redirect(url_for('cms.index'))
            else:
                return self.get(message="邮箱或密码错误")
        else:
            # print(form.errors)
            message = form.errors.popitem()[1][0]
            return self.get(message=message)

```



