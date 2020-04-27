## 使用property装饰器简化属性操作

### 1.代码案例(老师)

```python
'''
P04_propery属性
'''
class Account(object):
    def __init__(self, name, balance):
        self.__username = name
        self.__balance = balance
        self.__aaa = 0

    # 使用 property的装饰器形式
    # 注意:
    # 1. property 只能用来装饰 get 方法
    # 2. 所有的对属性操作的方法名,不需要再使用 set/get 开头了
    # 3. set 方法的名要和 get 方法名同名,尽量和属性名同名
    # 4. 必须 先装饰 get, 再装饰set
    # 5. 装饰set方法时, 语法是 get 方法名.setter

    @property
    def name(self):
        return self.__username

    @property
    def balance(self):
        print('Get Balance Run ')
        return self.__balance

    @balance.setter
    def balance(self, money):
        print('Set Balance Run ')
        if isinstance(money, int):
            self.__balance = money
        else:
            print('钱有问题')
# 使用者测试
if __name__ == '__main__':
    jack = Account('JackMa', 999999999)


    print(jack.name)
    print(jack.balance)

    jack.balance = 'aaaaa'
    print(jack.name)
    print(jack.balance)
```

### 2.代码案例(自己)

```python
class Account(object):
    def __init__(self,name, balance):
        self.__name = name
        self.__balance = balance
    @property
    def name(self):
        return self.__name
    @property
    def balance(self):
        return self.__balance
    @balance.setter
    def balance(self, money):
        if isinstance(money, int):
            self.__balance = money
        else:
            print('钱有问题')
if __name__ == '__main__':
    zs = Account('张三', 900000)

    zs.balance = 7777
    print(zs.name)
    print(zs.balance)
结果:
张三
7777
```

