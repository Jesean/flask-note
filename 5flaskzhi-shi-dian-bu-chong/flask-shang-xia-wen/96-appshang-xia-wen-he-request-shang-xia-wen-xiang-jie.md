# 96 app上下文和request上下文详解

## 应用上下文和请求上下文

应用上下文和请求上下文都是存放到一个'LocalStack'的栈中，和应用app相关的操作就必须要到应用上下文，比如通过'current\_app'获取当前的这个'app'，和请求相关的操作就必须用到请求上下文，比如使用'url\_for'反转视图函数。

1. 在视图函数中，不用担心上下午呢的问题，因为视图函数要执行，那么肯定是通过访问url的方式执行的，那么这种情况下，Flask底层就已经自动的帮我们把请求上下文和应用上下文都推入到了相应的栈中。
2. 如果想要在视图函数外面执行相关的操作，比如获取当前的app\(current\_app\)，或者是反转url，那么就必须要手动推入相关的上下文:

   * 手动推入上下文

   ```text
   # 第一种方式
   app_context = app.app_context()
   app_context.push()

   # 第二种方式
   with app.app_context():
       print(current_app.name)
   ```

   * 手动推入请求上下文，推入请求上下午到栈中，会首先判断有没有应用上下文，如果没有那么就会先推入应用上下文到栈中，然后推入请求上下文到栈中

   ```text
   with app.test_request_context():
       # 手动推入一个请求上下文到请求上下文栈中
       # 如果当前应用上下文中没有请求上下文
       # 那么会首先推入一个应用上下文到栈中
       print(url_for('my_list'))
   ```

## 为什么上下文需要放在栈中

1. 应用上下文，Flask底层是基于werkzeug，werkzeug是可以包含多个app的，所以这时候用一个栈来保存。如果你在使用app1，那么app1应该是要在栈的顶部。如果用完了app1，那么app1应该从栈中删除。方便其他代码使用下面的app
2. 如果在写测试代码，或者离线脚本的时候，我们有时候可能需要创建多个请求上下文，这时候需要存放到一个栈中了，使用哪个请求上下文的时候，就把对应的请求上下文放到栈的顶部

