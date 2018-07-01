## SQLAlchemy介绍和使用

数据库是一个网站的基础，在Flask中可以自由的使用MySQL、PostgreSQL、SQLite、Redis、MongoDB来写原生的语句实现功能，也可以使用更高级别的数据库抽象方式，如SQLAlchemy或MongoEngine这样的OR\(D\)M。本教程以MySQL+SQLAchemy的组合来进行讲解

在讲解Flask中的数据库操作之前，先确保已经安装了以下软件:

* msyql:如果是在windows上，到官网下载。如果是Ubuntu，通过命令下载 sudo apt-get install mysql-server libmysqlclient-dev -yq进行下载安装。
* MySQLdb:MySQLdb是用python来操作mysql的包，因此通过pip来安装，命令如下:pip install mysql-python
* SQLAlchemy:SQLAlchemy是一个数据库的ORM框架，安装命令:pip install SQLAlchemy



