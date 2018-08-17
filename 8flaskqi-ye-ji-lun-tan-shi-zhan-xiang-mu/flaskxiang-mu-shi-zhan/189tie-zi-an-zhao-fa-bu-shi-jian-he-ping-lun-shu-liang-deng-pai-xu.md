### 1.相关链接

标签:https://v3.bootcss.com/components/\#labels

### 2.点击切换按钮特效

```
                <ul class="nav nav-pills">
                    {% if current_sort == 1 %}
                        <li role="presentation" class="active"><a href="{{ url_for("front.index",st=1,board_id=current_board) }}">最新</a></li>
                    {% else %}
                        <li role="presentation"><a href="{{ url_for("front.index",st=1,board_id=current_board) }}">最新</a></li>
                    {% endif %}
                    {% if current_sort == 2 %}
                        <li role="presentation" class="active"><a href="{{ url_for("front.index",st=2,board_id=current_board) }}">精华帖子</a></li>
                    {% else %}
                        <li role="presentation"><a href="{{ url_for("front.index",st=2,board_id=current_board) }}">精华帖子</a></li>
                    {% endif %}
                    {% if current_sort == 3 %}
                        <li role="presentation" class="active"><a href="{{ url_for("front.index",st=3,board_id=current_board) }}">点赞最多</a></li>
                    {% else %}
                        <li role="presentation"><a href="{{ url_for("front.index",st=3,board_id=current_board) }}">点赞最多</a></li>
                    {% endif %}
                    {% if current_sort == 4 %}
                        <li role="presentation" class="active"><a href="{{ url_for("front.index",st=4,board_id=current_board) }}">评论最多</a></li>
                    {% else %}
                        <li role="presentation"><a href="{{ url_for("front.index",st=4,board_id=current_board) }}">评论最多</a></li>
                    {% endif %}

                </ul>
```



