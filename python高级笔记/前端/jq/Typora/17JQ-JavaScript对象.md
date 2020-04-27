## JQ-JavaScript对象

### 1. JavaScript对象的介绍

JavaScript 中的所有事物都是对象：字符串、数值、数组、函数等都可以认为是对象，此外，JavaScript 允许自定义对象，对象可以拥有属性和方法。

### 2. JavaScript创建对象操作

创建自定义javascript对象有两种方式:

- 通过顶级Object类型来实例化一个对象
- 通过对象字面量创建一个对象

**说明:**

调用属性和方法的操作都是通过点语法的方式来完成，对象的创建推荐使用字面量方式，因为更加简单。

```js

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>JQ17_JavaScript对象</title>
    
    <script>
        // 定义对象方式一  利用 object 根类来实例对象
        var obj1 = new Object();
        // 为对象添加属性和方法(动态绑定)
        obj1.name = 'Tom';
        obj1.age = 15;
        // 绑定方法
        obj1.info = function(){
            // this 表示当前对象本身, 相当于 python 中的self
            alert(this.name + this.age);
        }

        alert('属性为:' + obj1.name + '--' + obj1.age);
        obj1.info();

        // 定义对象方式二 字面量形式
        var obj2 = {
            name:'Jack',
            age:15,
            gender:'男',
            info:function(n){
                for(var i = 0; i < n; i++){
                    alert(this.name + this.age + this.gender);
                }
            }
        }
        alert('属性为:' + obj2.name + '--' + obj2.age + '--' + obj2.gender);
        obj2.info(3);


    </script>

</head>
<body>
    
</body>
</html>
```

### 3. 小结

创建自定义javascript对象有两种方式:

- Object
- 字面量