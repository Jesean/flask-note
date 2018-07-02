### Column常用参数

* default:默认值
* nullable:是否可空
* primary\_key:是否为主键
* unique:是否唯一
* autoincrement:是否自动增长
* name:该属性在数据库中的字段映射

### sqlalchemy常用数据类型

* Integer:整型
* Float:浮点类型
* Boolean:传递True/False进去
* DECIMAL:定点类型，是专门为了解决浮点精度丢失的问题的，在存储相关的字段的时候建议都是要这个数据字段，并且这个类型使用的时候需要传递两个参数，第一个参数使用来标记字段能够存储多少个数字，第二个参数是表示小数点的最大位数
* enum:枚举类型。指定某个字段只能是枚举中指定的几个值，不能为其他值，在ORM模型中，使用Enum来作为枚举，示例代码如下:

```
import enum
class TagEnum(enum.Enum):
    python = "python"
    flask = "flask"
    django = "django"


class Article(Base):
    __tablename__ = "article"
    id = Column(Integer,primary_key=True,autoincrement=True)
    # tag = Column(Enum('python','django','flask'))
    tag = Column(Enum(TagEnum))

# article = Article(tag='1')
# article = Article(tag='python')
article = Article(tag=TagEnum.python)
```

* Date:传递datetime.date\(\)进去。存储时间，只能存储年月日。映射到数据库中是date类型。在python中，可以使用datetime.date来指定
* DateTime:传递datetime.datetime\(\)进去。
* Time:传递datetime.time\(\)进去
* String:字符类型，使用时需要指定长度，区别于Text类型
* Text:文本类型
* LONGTEXT:长文本类型



