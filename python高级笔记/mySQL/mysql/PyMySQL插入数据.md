## PyMySQL插入数据

1.导包

```python
from pymysql import connect
```

2.建立数据库连接

```python
db_connect = connect(host='locahost',port=3306,user='root',passwd='mysql',database='python',charset='utf8')
```

3.建立游标对象

```python
cur = db_connent.cursor()
```

4.操作数据库指令

```python
sql_str = ''' insert into students(name) values ('王钢蛋'); '''

cur.execute(sql_str)

db_connect.commit()
```

5.关闭游标

```pytho
cur.close()
```

6.关闭数据库连接

```pytho
db_connect.close()
```



```python
'''
P02_PyMySQL插入数据
'''

from pymysql import Connect

db_connect = Connect(host='localhost',port=3306,database='python_db',user='root',password='123123',charset='utf8')

# 在使用 PyMySQL 时,当创建一个游标对象时,会隐式的自动创建一个事务环境
# 在一个程序中一种操作尽量使用一个事务,不要交叉使用

cur = db_connect.cursor()


# 准备SQL字符串
sql_str = ''' insert into students(name) values ('王钢蛋'); '''

cur.execute(sql_str)

# 因为默认的事务环境的影响,如果没有提交操作,数据会默认认为是回滚
# 如果对数据进行了 增 删除, 改,操作,都要进行提交,提交时使用 数据库连接对象操作

db_connect.commit()

cur.close()

db_connect.close()
```