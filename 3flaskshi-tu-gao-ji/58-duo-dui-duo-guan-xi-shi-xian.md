### 多对多的关系

1. 多对多的关系需要通过一张中间表来绑定它们之间的关系
2. 先把两个需要多对多的模型定义出来
3. 使用Table定义定义一个中间表，中间表一般就是包含两个模型的外键字段就可以了，并且让它们两个来作为一个"复合主键"
4. 在两个需要做多对多的模型中随便选择一个模型，定义一个relationship属性，来绑定三者之间的关系，在使用relationship的时候，需要传入一个secondary=中间表

---

#### Article表

    """
    Create Table: CREATE TABLE `article` (
      `id` int(11) NOT NULL AUTO_INCREMENT,
      `title` varchar(50) NOT NULL,
      PRIMARY KEY (`id`)
    """
    class Article(Base):
        __tablename__ = "article"
        id = Column(Integer,primary_key=True,autoincrement=True)
        title = Column(String(50),nullable=False)

        def __repr__(self):
            return "<Article(title:{})>".format(self.title)

#### Tag表

    """
    Create Table: CREATE TABLE `tag` (
      `id` int(11) NOT NULL AUTO_INCREMENT,
      `name` varchar(50) NOT NULL,
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB DEFAULT CHARSET=latin1
    """
    class Tag(Base):
        __tablename__ = "tag"
        id = Column(Integer,primary_key=True,autoincrement=True)
        name = Column(String(50),nullable=False)

        articles = relationship("Article",backref="tags",secondary=article_tag)

        def __repr__(self):
            return "<Tag(name:{})>".format(self.name)

#### article\_tag中间表

    """
    Create Table: CREATE TABLE `article_tag` (
      `article_id` int(11) NOT NULL,
      `tag_id` int(11) NOT NULL,
      PRIMARY KEY (`article_id`,`tag_id`),
      KEY `tag_id` (`tag_id`),
      CONSTRAINT `article_tag_ibfk_1` FOREIGN KEY (`article_id`) REFERENCES `article` (`id`),
      CONSTRAINT `article_tag_ibfk_2` FOREIGN KEY (`tag_id`) REFERENCES `tag` (`id`)
    ) ENGINE=InnoDB DEFAULT CHARSET=latin1
    """
    article_tag = Table(
        "article_tag",
        Base.metadata,
        Column("article_id",Integer,ForeignKey("article.id"),primary_key=True),
        Column("tag_id",Integer,ForeignKey("tag.id"),primary_key=True)
    )



