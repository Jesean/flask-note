### alembic教程

alembic是sqlalchemy的作者开发的。用来做ORM模型与数据的迁移与映射。alembic使用方式跟git有点类似，表现在两个方面，第一个，alembic的所有命令都是以alembic开头，第二，alembic的迁移文件也是通过版本进行控制的。首先，通过pip install alembic进行安装。以下将解释alembic的用法:

1.初始化alembic仓库:在终端中，cd到项目目录中，然后执行alembic init alembic，创建一个名叫alembic的仓库。

2.创建模型类:创建一个models.py模块，然后在里面定义模型类，示例代码:

```

```

3.

