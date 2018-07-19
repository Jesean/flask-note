#### 添加crsf

```
# 防御crsf漏洞
from flask_wtf import CSRFProtect
CSRFProtect(app)

在表单中添加:
<input type="hidden" name="csrf_token" value="{{ csrf_token() }}" />
```



