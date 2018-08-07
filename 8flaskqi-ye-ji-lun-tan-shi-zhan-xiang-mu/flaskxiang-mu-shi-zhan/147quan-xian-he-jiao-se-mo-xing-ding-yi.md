```
用户、角色、权限三者之间的关系

用户可以有多个角色
一个角色可以拥有多个用户
一个角色有一个权限
```

### 定义功能权限

```
class CMSPersmission(object):
    # 255的二进制方式来表示 1111 1111
    ALL_PERMISSION = 0b11111111
    # 1. 访问者权限
    VISITOR =        0b00000001
    # 2. 管理帖子权限
    POSTER =         0b00000010
    # 3. 管理评论的权限
    COMMENTER =      0b00000100
    # 4. 管理板块的权限
    BOARDER =        0b00001000
    # 5. 管理前台用户的权限
    FRONTUSER =      0b00010000
    # 6. 管理后台用户的权限
    CMSUSER =        0b00100000
    # 7. 管理后台管理员的权限
    ADMINER =        0b01000000
```

### 定义CMSRole管理权限模型

```
class CMSRole(db.Model):
    __tablename__ = "cms_role"
    id = db.Column(db.Integer,primary_key=True,autoincrement=True)
    name = db.Column(db.String(50),nullable=False)
    # 描述信息
    desc = db.Column(db.String(200),nullable=True)
    create_time = db.Column(db.DateTime,default=datetime.now)
    # 权限，默认为访问者权限
    permissions = db.Column(db.Integer,default=CMSPersmission.VISITOR)

    # 定义关系,users,rols,分别是两个表对应哪个的字段，secondary指定中间表
    users = db.relationship('CMSUser',secondary=cms_role_user,backref='rols')
```

### 定义中间表与用户表绑定

```
# 绑定两个表，表与表之间的关系为多对多
# 引用外键，表名.键名
cms_role_user = db.Table(
    'cms_role_user',
    db.Column('cms_role_id',db.Integer,db.ForeignKey('cms_role.id'),primary_key=True),
    db.Column('cms_user_id',db.Integer,db.ForeignKey('cms_user.id'),primary_key=True),
)
```



