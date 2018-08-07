在CMSUser模型上扩展判断权限的功能

```
    # 注意roles是什么，是上面的反向这个表的，用于通过这个属性绑定CMSRole模型
    # 拿到用户所有的权限
    @property
    def permissions(self):

        # 没有任何权限
        if not self.roles:
            return 0
        all_permissions = 0
        # 遍历权限
        for role in self.roles:
            permissions = role.permissions
            all_permissions |= permissions
        return all_permissions

    # 判断用户权限
    def has_permission(self,permission):
        # all_permissions = self.permissions
        # result =  all_permissions & permission == permission
        # return result
        return self.permissions & permission == permission

    # 判断是否为开发者
    def is_developer(self):
        return self.has_permission(CMSPersmission.ALL_PERMISSION)
```

定义为用户添加权限的命令

```
 命令，不传参数
@manager.command
def create_role():
    # 1. 访问者（可以修改个人信息）
    visitor = CMSRole(name='访问者',desc='只能相关数据，不能修改。')
    visitor.permissions = CMSPermission.VISITOR

    # 2. 运营角色（修改个人个人信息，管理帖子，管理评论，管理前台用户）
    operator = CMSRole(name='运营',desc='管理帖子，管理评论,管理前台用户。')
    operator.permissions = CMSPermission.VISITOR|CMSPermission.POSTER|CMSPermission.CMSUSER|CMSPermission.COMMENTER|CMSPermission.FRONTUSER

    # 3. 管理员（拥有绝大部分权限）
    admin = CMSRole(name='管理员',desc='拥有本系统所有权限。')
    admin.permissions = CMSPermission.VISITOR|CMSPermission.POSTER|CMSPermission.CMSUSER|CMSPermission.COMMENTER|CMSPermission.FRONTUSER|CMSPermission.BOARDER

    # 4. 开发者
    developer = CMSRole(name='开发者',desc='开发人员专用角色。')
    developer.permissions = CMSPermission.ALL_PERMISSION

    db.session.add_all([visitor,operator,admin,developer])
    db.session.commit()

# 将用户添加到访问者权限中
# python manage.py add_user_to_role -e 1479852727@qq.com -n 访问者
# 定义添加角色的命令，不然没有访问权限
# 将某用户添加到某角色中
@manager.option('-e','--email',dest='email')
@manager.option('-n','--name',dest='name')
def add_user_to_role(email,name):
    user = CMSUser.query.filter_by(email=email).first()
    if user:
        role = CMSRole.query.filter_by(name=name).first()
        if role:
            role.users.append(user)
            db.session.commit()
            print("用户添加到角色成功")
        else:
            print("没有这个角色:{}".format(name))
    else:
        print("{}邮箱没有这个用户".format(email))


# python manage.py test_permission
@manager.command
def test_permission():
    # 查询用户
    user = CMSUser.query.first()
    if user.is_developer():
        print("拥有访问者权限")
    else:
        print("无访问者权限")
```



