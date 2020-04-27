## PyMySQL_删除数据

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
sql_str = ''' delete from teacher where name = "张三丰" or age="20"' '''

cur.execute(sql_str)

db_connect.commit()
```

5.关闭游标

```pytho
cur.close()
```

6.关闭数据库连接

```python
db_connect.close()
```



```python
'''
P04_PyMySQL_删除数据
'''

from pymysql import Connection

db_connect = Connection(host='127.0.0.1', port=3306,user='root', password='123123', database='Python_db',charset='utf8')

cur = db_connect.cursor()

sql_str = ''' delete from students where id > 15; '''
cur.execute(sql_str)
db_connect.commit()

cur.close()

db_connect.close()
```