## SQL注入和使用参数化进行解决

什么是SQL注入?

用户提交带有恶意的数据与SQL语句进行字符串方式的拼接，从而影响了SQL语句的语义，最终产生数据泄露的现象。

如何防止SQL注入?

SQL语句参数化

- SQL语言中的参数使用%s来占位，此处不是python中的字符串格式化操作
- 将SQL语句中%s占位所需要的参数存在一个列表中，把参数列表传递给execute方法中第二个参数

1.导包

```python
from pymysql import connect # connect =Connect =Connection
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
select_id = input('请输入一个ID:')
sql_str = ''' select * from students where id = %s '''  
# SQL语言中的参数使用%s来占位，此处不是python中的字符串格式化操作
print(sql_str)
cur.execute(sql_str,[select_id])
result = cur.fetchall()
for item in result:
    print(item)
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
P05_SQL注入和使用参数化进行解决
'''
from pymysql import Connection

db_connect = Connection(host='127.0.0.1', port=3306,user='root', password='123123', database='Python_db',charset='utf8')

cur = db_connect.cursor()

select_id = input('请输入一个ID:')

# 下面操作会产生SQL注入
# sql_str = ''' select * from students where id = %s ''' % select_id
# print(sql_str)
#
# cur.execute(sql_str)
#
# result = cur.fetchall()

sql_str = ''' select * from students where id = %s '''
print(sql_str)

# 利用PyMySQL中的 exxcute 方法的参数二,来向 SQL语句字符串中的占位符中传递数据
# 利用参数化来解决 SQL 注入问题
# cur.execute(sql_str,(select_id,))
cur.execute(sql_str,[select_id])
result = cur.fetchall()
for item in result:
    print(item)
cur.close()
db_connect.close()
```

