## 通过PyMySQL模块来查询数据库中的数据

### 步骤:

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
sql_str = ''' select * from students ''';
row_count = cur.execute(sql_str)
print('查询受影响 %d 行....' % row_count)

result = cur.fetchone()
print(result)
print('*' * 20)

result = cur.fetchmany(4)
for item in result:
    print(item)
print('*' * 20)

result = cur.fetchall()
for item in result:
    print(item)
print('*' * 20)

print(cur.rowcount)
print(cur.rownumber)
cur.rownumber = 0

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
通过PyMySQL模块来查询数据库中的数据
'''

# 0. 导包
from pymysql import connect

# 1. 建立数据库连接
#  * 参数host：连接的mysql主机，如果本机是'localhost'
#  * 参数port：连接的mysql主机的端口，默认是3306
#  * 参数user：连接的用户名
#  * 参数password：连接的密码
#  * 参数database：数据库的名称
#  * 参数charset：通信采用的编码方式，推荐使用utf8
# 注意: 1. 连接数据库时,除端口参数使用数字类型外,其他参数都是字符串类型
#      2. localhost 表示本机,是当前写程序的电脑
#      3. 这6个参数没有顺序问题
db_connent = connect(host='localhost',port=3306,user='root',password='123123',database='python_db', charset='utf8')

# 2. 建立游标对象
cur = db_connent.cursor()

# 3. 操作数据库指令
# 3.1 先去准备查询语句字符串
# sql_str = ''' select * from students where name = '小明' ''';
sql_str = ''' select * from students ''';

# 3.2 执行SQL语句.该函数不会得到查询结果,只会返回一个查询结果的条数,受影响的条目
row_count = cur.execute(sql_str)
print('查询受影响 %d 行....' % row_count)

# 3.3 获取查询数据
# 3.3.1 获取一条数据,结果数据以元组形式表示
result = cur.fetchone()
print(result)
print('*' * 20)


# 3.3.2 获取指定条数的记录, 返回记录是一个嵌套元组  ((),(),())
result = cur.fetchmany(4)
for item in result:
    print(item)
print('*' * 20)

# 3.3.3 获取所有数据,返回记录是一个嵌套元组  ((),(),())
result = cur.fetchall()
for item in result:
    print(item)
print('*' * 20)

# 3.3.4 如果游标在没有关闭和重置的情况下,读取所有数据后,再次读取,不会获取任何数据
# 如果想得数据,一,关闭游标重新打开,二,重置游标对象

#  cur.rowcount 表示的是查询 之后影响的条数
print(cur.rowcount)
# cur.rownumber 表示是游标的位置
print(cur.rownumber)

# 重置游标
cur.rownumber = 0
result = cur.fetchall()
for item in result:
    print(item)


# 4. 关闭游标
cur.close()

# 5. 关闭数据库连接
db_connent.close()
```