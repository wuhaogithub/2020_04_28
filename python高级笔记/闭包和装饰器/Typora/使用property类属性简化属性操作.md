## propery属性-类

### 1.案例代码(老师)

```python
'''
P04_propery属性
'''
class Account(object):
    def __init__(self, name, balance):
        self.__username = name
        self.__balance = balance
        self.__aaa = 0

    # 实现公有接口方法来间接访问私有属性
    # 1. 可以提供精确的访问控制权限
    # 2. 隐藏实现细节
    # 3. 可以保证数据有效性

    def get_name(self):
        return self.__username


    def set_balance(self, money):
        print('Set Balance Run ')
        if isinstance(money, int):
            self.__balance = money
        else:
            print('钱有问题')

    def get_balance(self):
        print('Get Balance Run ')
        return self.__balance

    # property类属性方式
    name = property(fget=get_name)
    balance = property(fget=get_balance, fset=set_balance)


# 使用者测试
if __name__ == '__main__':
    jack = Account('JackMa', 999999999)

    # jack.set_balance('aaaaaaa')
    # print(jack.get_balance())

    print(jack.name)
    print(jack.balance)

    jack.balance = 'aaaaa'
    print(jack.name)
    print(jack.balance)

```

### 2.案例代码(自己)

```python
class Account(object):
    def __init__(self,name, balance):
        self.__name = name
        self.__balance = balance
    def get_name(self):
        return self.__name
    def set_balance(self, money):
        if isinstance(money, int):
            self.__balance = money
        else:
            print('钱有问题')
    def get_balance(self):
        return self.__balance
    name = property(fget=get_name)
    balance = property(fget=get_balance, fset=set_balance)
if __name__ == '__main__':
    zs = Account('张三', 900000)
    # print(zs.get_name())
    # print(zs.get_balance())
    zs.balance = 7777
    print(zs.name)
    print(zs.balance)
结果:
张三
7777

```

