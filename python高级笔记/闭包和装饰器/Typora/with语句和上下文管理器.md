## with语句和上下文管理器

一个类只要实现了`__enter__()和__exit__()`这个两个方法，通过该类创建的对象我们就称之为上下文管理器。

上下文管理器可以使用 with 语句，**with语句之所以这么强大，背后是由上下文管理器做支撑的**，也就是说刚才使用 open 函数创建的文件对象就是就是一个上下文管理器对象。

**自定义上下文管理器类,模拟文件操作:**

定义一个File类，实现 `__enter__() 和 __exit__()`方法，然后使用 with 语句来完成操作文件

###  1.代码案例(自己)

```python
class File(object):
    def __init__(self, file_name, file_model):
        self.file_name = file_name
        self.file_model = file_model
    def __enter__(self):
        print('进入上文方法')
        self.file = open(self.file_name, self.file_model)

        return self.file
    def __exit__(self, exc_type, exc_val, exc_tb):
        print('进入下文方法')
        self.file.close()
if __name__ == '__main__':
    with File('test.txt', 'r') as file:
        file_date = file.read()
        print(file_date)
结果:
进入上文方法
hello 鍚存槉  # 编码格式造成乱码
进入下文方法
```

2.代码案例(老师)

```python
'''
P05_上下文管理器
'''


# 模拟open实现
class MyOpen(object):
    def __init__(self,file, mode):
        self.filename = file
        self.mode = mode

    # enter 方法用来实现进入上下文时,进行准备初始化工作
    def __enter__(self):
        print('Enter Run ...')
        self.file = open(self.filename,self.mode)
        # 这个返回值,会赋给值 with 语句中 as 后的变量
        return self.file


    # exit 方法用来退出上下文,退出出需要做善后处理工作,资源的回收释放
    def __exit__(self, exc_type, exc_val, exc_tb):
        print('Exit Run ...')
        self.file.close()

    # enter 和 exit 方法用来建立一个环境上下文 context
    # 应用场景: 数据库操作


if __name__ == '__main__':

    # with open('a.txt','w') as file:
    #     file.write('Hello')

    with MyOpen('a.txt', 'r') as file:
        content = file.read()
        print(content)

    print('over')
结果:
Enter Run ...
Hello
Exit Run ...
over
```

**代码说明:**

- `__enter__`表示上文方法，需要返回一个操作文件对象
- `__exit__`表示下文方法，with语句执行完成会自动执行，即使出现异常也会执行该方法。

### 3. 小结

- Python 提供了 with 语句用于简化资源释放的操作，使用 with 语句操作建立在上下文管理器(实现`__enter__和__exit__`)的基础上