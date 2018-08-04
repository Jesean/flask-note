### 1.g对象

```
from .views import bp
import config
from flask import  session,g
from .models import CMSUser

# 钩子函数，在请求之前获取
@bp.before_request
def before_request():
    if config.CMS_USER_ID in session:
        user_id = session.get(config.CMS_USER_ID)
        user = CMSUser.query.get(user_id)
        if user:
            g.cms_user = user
```



