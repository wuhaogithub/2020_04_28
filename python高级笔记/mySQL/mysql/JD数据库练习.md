## JD数据库练习

### 1.自己代码:

```python
from pymysql import connect
class JingDong(object):
    def __init__(self,username,passwd,db):
        self.__db_connect = connect(host = '192.168.36.34', port = 3306, user = username, password = passwd, database = db, charset = 'utf8')

    def __del__(self):
        self.__db_connect.close()
        print('数据库安全关闭')
    def __menu(self):
        print('1. 查询所有商品信息')
        print("2. 查询所有包含商品的分类")
        print("3. 添加新商品分类")
        print("4. 将所有商品价格加1000")
        print("5. 将所有笔记本的分类改为超级本")
        print("6. 根据id查询商品信息")
        print("7. 根据id查询商品信息安全方式")
        print("8. 退出系统")
    def __show_result(self,result):
        print("*" * 100)
        for i in result:

            print(i)
        print("*" * 100)
    def run(self):
        while True:
            self.__menu()
            input_id = input('请输入要选择的功能ID:')
            if input_id == '1':
                self.__a()
            elif input_id == '2':
                self.__b()
            elif input_id == '3':
                self.__c()
            elif input_id == '4':
                self.__d()
            elif input_id == '5':
                self.__e()
            elif input_id == '6':
                self.__f()
            elif input_id == '7':
                self.__g()
            elif input_id == '8':
                break
            else :
                print('你输入的id不正确,请重新输入')

    def __a(self):
        cur = self.__db_connect.cursor()
        str = '''select * from goods'''
        cur.execute(str)
        result = cur.fetchall()
        self.__show_result(result)
        cur.close()

    def __b(self):
        cur = self.__db_connect.cursor()
        str = '''select * from good_cates where id in (select distinct cate_id from goods);'''
        cur.execute(str)
        result = cur.fetchall()
        self.__show_result(result)
        cur.close()
    def __c(self):


        cur = self.__db_connect.cursor()
        input_id = input('请输入新添加的商品分类:')
        str = '''insert into good_cates(name) values(%s)'''
        cur.execute(str,input_id)
        self.__db_connect.commit()
        cur.close()


    def __d(self):
        cur = self.__db_connect.cursor()
        str = '''update goods set price = price + 1000'''
        cur.execute(str)
        self.__db_connect.commit()
        cur.close()
    def __e(self):
        cur = self.__db_connect.cursor()
        str = '''update good_cates set name =  '炫酷本' where name = '超极本' '''
        cur.execute(str)
        self.__db_connect.commit()
        cur.close()
        pass
    def __f(self):
        cur = self.__db_connect.cursor()
        input_id = input('请输入商品ID:')
        str = '''select * from goods where id = %s'''
        cur.execute(str,input_id)
        result = cur.fetchall()
        self.__show_result(result)
        cur.close()

    def __g(self):
        cur = self.__db_connect.cursor()
        input_id = input('请输入商品ID:')
        str = '''select * from goods where id = %s'''
        cur.execute(str, input_id)
        result = cur.fetchall()
        self.__show_result(result)
        cur.close()
if __name__ == '__main__':
    server = JingDong('root', 'mysql', 'jing_dong')
    server.run()

```

### 2.老师代码:

```python
'''
JD数据库练习
'''

# 导入模块
from pymysql import Connect


class JDServer(object):

    def __init__(self,username, passwd, db):
        self.__db_connect = Connect(host='localhost', port=3306,user=username, password=passwd,database=db,charset='utf8')

    def __del__(self):
        # 在销毁当前对象时自动调用的方法
        self.__db_connect.close()
        print('数据库安全关闭....')


    # 显示菜单方法
    def __print_menu(self):
        print('1. 查询所有商品信息')
        print("2. 查询所有包含商品的分类")
        print("3. 添加新商品分类")
        print("4. 将所有商品价格加1000")
        print("5. 将所有笔记本的分类改为超级本")
        print("6. 根据id查询商品信息")
        print("7. 根据id查询商品信息安全方式")
        print("8. 退出系统")

    # 打印结果方法
    def __show_query_result(self, result):
        print('*' * 50)

        for item in result:
            print(item)

        print('*' * 50)

    # 服务器运行方法,实现主体逻辑
    def run(self):
        while True:
            self.__print_menu()
            query_id = input('请输入要选择的功能ID:')
            if query_id == '1':
                self.__fetch_all_info()
            elif query_id == '2':
                self.__fetch_cate_of_goods()
            elif query_id == '3':
                self.__add_new_cate()
            elif query_id == '4':
                self.__update_price()
            elif query_id == '5':
                self.__update_cate()
            elif query_id == '6':
                self.__fetch_info_with_id()
            elif query_id == '7':
                self.__fetch_info_with_id_safe()
            elif query_id == '8':
                print('成功退出系统....')
                break
            else:
                print('输入错误,重新输入...')

    # 1. 查询所有商品信息
    def __fetch_all_info(self):
        # 每个业务中的游标对象单独创建,使用完成后,要关闭
        cur = self.__db_connect.cursor()

        # 执行的SQL语句
        sql_str = ''' select * from goods; '''
        cur.execute(sql_str)

        # 获取结果
        result = cur.fetchall()
        # 利用封装好的函数来输出查询结果
        self.__show_query_result(result)

        cur.close()

    # 2. 查询所有包含商品的分类
    def __fetch_cate_of_goods(self):

        cur = self.__db_connect.cursor()
        sql_str = ''' select * from good_cates where id in (select distinct cate_id from goods); '''
        cur.execute(sql_str)
        result = cur.fetchall()
        self.__show_query_result(result)
        cur.close()

    # 3. 添加商品分类
    def __add_new_cate(self):
        cur = self.__db_connect.cursor()
        new_cate = input('请输入一个新的分类:')
        sql_str = ''' insert into good_cates(name) values(%s)'''
        cur.execute(sql_str,[new_cate])
        # 提交数据
        self.__db_connect.commit()

        cur.close()

    # 4. 将所有商品价格加1000
    def __update_price(self):
        cur = self.__db_connect.cursor()
        sql_str = ''' update goods set price = price + 1000 '''
        cur.execute(sql_str)
        self.__db_connect.commit()
        cur.close()

    # 5. 将所有笔记本的分类改为超级本
    def __update_cate(self):
        cur = self.__db_connect.cursor()
        sql_str = ''' update goods set cate_id = (select id from good_cates where name = '超级本') where name like '%笔记本%' '''
        cur.execute(sql_str)
        self.__db_connect.commit()
        cur.close()

    # 6. 根据id查询商品信息
    def __fetch_info_with_id(self):
        cur = self.__db_connect.cursor()
        query_id = input('请输入商品ID:')
        sql_str = '''select * from goods where id = %s ''' % query_id
        cur.execute(sql_str)
        result = cur.fetchall()
        self.__show_query_result(result)
        cur.close()

    # 7. 根据id查询商品信息安全方式
    def __fetch_info_with_id_safe(self):
        cur = self.__db_connect.cursor()
        query_id = input('请输入商品ID:')
        sql_str = '''select * from goods where id = %s '''
        cur.execute(sql_str,[query_id])
        result = cur.fetchall()
        self.__show_query_result(result)
        cur.close()



# 入口
if __name__ == '__main__':
    server = JDServer('root','123123','jing_dong')
    server.run()
```