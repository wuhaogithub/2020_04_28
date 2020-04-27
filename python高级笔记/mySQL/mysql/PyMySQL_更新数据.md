## PyMySQL_更新数据

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
sql_str = ''' update teacher set name = '高喷涂' where name = '小沈阳';'''
cur.execute(sql_str)
db_connect.commit()
```

5.关闭游标

```pytho
cur.close()
```

6.关闭数据库连接

```pyth
db_connect.close()
```

```python
'''
P03_PyMySQL_更新数据
'''

from pymysql import Connection

db_connect = Connection(host='127.0.0.1', port=3306,user='root', password='123123', database='Python_db',charset='utf8')

cur = db_connect.cursor()

sql_str = ''' update students set name = '铁锤妹妹' where name = '王钢蛋' '''

cur.execute(sql_str)

db_connect.commit()

cur.close()

db_connect.close()
```