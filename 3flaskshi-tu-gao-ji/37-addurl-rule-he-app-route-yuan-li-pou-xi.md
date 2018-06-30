## 视图高级笔记

### add\_url\_rule\(rule,endpoint=None,view\_func=None\)

这个方法用来添加url与视图函数的映射，如果没有填写，那么默认会使用"view\_func"的名字作为"endpoint"，以后再使用"url\_for"的时候，就要看在映射的时候有没有

