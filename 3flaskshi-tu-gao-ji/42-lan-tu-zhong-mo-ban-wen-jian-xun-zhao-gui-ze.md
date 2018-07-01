```
from flask import Blueprint,render_template

news_bp = Blueprint('news',__name__,url_prefix='/news',template_folder='miku')

@news_bp.route('/list/')
def news_list():
    return render_template('news.html')

@news_bp.route('/detail/')
def detail():
    return '新闻详情页面'
```

### 模板文件![](/assets/42-templates.png)



