### 开启crsf保护

```
from flask_wtf.csrf import CSRFProtect
....
CSRFProtect(app)

在表单中添加如下:
<input type="hidden" name="csrf_token" value="{{ csrf_token() }}" />
```



