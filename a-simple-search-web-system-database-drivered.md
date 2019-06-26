# 数据库驱动的简单web查询系统实现

## 数据库可视化设计工具

https://editor.ponyorm.com/explore

## 需求

1. 导入excel数据，from 挖财
2. 自定义查询
3. 对导入的数据进行分析，生成报表

## 技术选型

python , linux, mysql, sqlalchemy

###  目的

锻炼编码能力，将mysql,sqlalchemy,数据库表设计应用到实际项目中

### get技能

#### 在python中操纵excel

除了openpyxl,还有xlrd/xlwt,xlrd用来读excel中的数据，xlwt用来写入excel,这两个工具仅支持xls格式的excel

如果要读写.xlsx, xlsm, xltx, and xltm文件，推荐使用openpyxl

```shell
source activate venv
pip install openpyxl
```

参考: https://www.datacamp.com/community/tutorials/python-excel-tutorial

####  在windows中安装配置mysql server8.0.16
参考：http://www.ntu.edu.sg/home/ehchua/programming/sql/mysql_howto.html

#### 如何在mysql库中创建数据库

在部署项目时可以在安装完数据库后用命令创建数据库，这些都可以通过shell脚本实现

create database if not exists yoursbname default charset utf8 collate utf8_general_ci;

####  使用model创建数据库表

关键词 python3 sqlalchemy declarative_base

将以下代码保存为model.py，运行python model.py，会链接mysql数据库中指定库，然后将定义的model类转换成sql语句，创建数据库

```python
#! /usr/bin/env/python
# -*- coding: utf-8 -*-

from sqlalchemy.ext.declarative import declarative_base
from sqlalchemy import create_engine, Column, Integer, String

Base = declarative_base()

Class User(base):
    __tablename__ = 'user'
    user_id = Column(String(50), primary_key=True)

if __name__ == "__main__":
    username = ""
    password = ""
    host = ""
    db = ""
    engine = create_engine("mysql+mysqldb://%s:%s@%s/%s?charset=utf8" %(username, password, host, db), echo = True, pool_size = 100)
    Base.metadata.create_all(engine)
```

​    

#### sqlalchemy增删改查数据库表
关键词：session
参考：https://yangsijie666.github.io/2018/07/31/sqlalchemy模块/



## 环境配置

vscode + venv + flask

### 如何让vscode使用virtualenv里的python环境

参考 https://www.jianshu.com/p/c60a63b4adae

###  使用flask实现文件上传功能

参考 https://zhuanlan.zhihu.com/p/23731819

该步骤实现了将excel等文件上传到服务器目录的目的

### 如何将上传后的excel中的数据插入到数据库表中

思路：按照sheet页读取excel数据，并将数据转成dict数据，再写入数据库表中

http://liyangliang.me/posts/2013/02/using-openpyxl-to-read-and-write-xlsx-files/

用openpyxl处理xlsx文件


## 知识点

### isinstance()函数
www.runoob.com/python/python-func-isinstance.html

语法：isinstance(object, classinfo)

对于基本类型来说classinfo可以是：
int, float, bool, complex, str, list, dict, set, tuple
要注意的是，classinfo的字符串是str而不是string，字典也是简写dict


###  with closing() as session

使用closing()将对象变成上下文对象，这样就支持with语句了。

```python
from contextlib import closing
from sqlalchemy import create_engine, orm

engine = None
class BaseOps:
    def __init__(self):
        global engine
        if engine is None:
            engine = create_engine()
            self.session_maker = orm.sessionmaker(bind=engine)

def get_db_session(self):
    try:
        self.session = self.session_maker()
        return self.session
     except Exception as error:
         logging.error("can't connect db : %s" % error)

with closing(self.get_db_session()) as session:
    new_user = ""
    session.add(new_user)
    session.commit()
```




###  pyrhon3去掉了python2中的has_key()方法

python3中使用if key in dict:




