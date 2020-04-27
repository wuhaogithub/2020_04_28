## 一、重定向命令

### 1. 重定向命令的介绍

重定向也称为输出重定向，把在终端执行命令的结果保存到目标文件。

### 2. 重定向命令的使用

| 命令 | 说明                                                       |
| :--- | :--------------------------------------------------------- |
| >    | 如果文件存在会覆盖原有文件内容，相当于文件操作中的‘w’模式  |
| >>   | 如果文件存在会追加写入文件末尾，相当于文件操作中的‘a’ 模式 |

**重定向命令效果图:**

![重定向命令](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/%E9%87%8D%E5%AE%9A%E5%90%911.png)

![重定向命令](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/%E9%87%8D%E5%AE%9A%E5%90%912.png)

**说明:**

只要在终端能显示信息的命令都可以使用重定向，比如: tree

### 3. 小结

- 终端内容保存到文件使用重定向有两种方式: **>** 和 **>>**
- **>** 表示每次只写入最新的数据，原有数据不保留。
- **>>** 表示每次在原有数据的基础上进行追加，原有数据会保留。

## 二、查看文件内容命令

**学习目标**

- 能够说出查看大文件分屏显示使用的命令

------

### 1. 查看文件内容命令的使用

| 命令 | 说明             |
| :--- | :--------------- |
| cat  | 查看小型文件     |
| more | 分屏查看大型文件 |

**cat命令的效果图**

![cat命令](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/cat.png)

**说明:**

- cat命令结合重定向可以完成多个文件的合并
- gedit 文件编辑命令，可以查看和编辑文件

**more命令的效果图**

当查看内容信息过长无法在一屏上显示时，可以使用 more 命令在终端分屏显示文件内容。

![more命令](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/more.png)

**操作键说明:**

| 操作键 | 说明           |
| :----- | :------------- |
| 空格   | 显示下一屏信息 |
| 回车   | 显示下一行信息 |
| b      | 显示上一屏信息 |
| f      | 显示下一屏信息 |
| q      | 退出           |

### 2. 管道(|)命令的使用

管道(|)：一个命令的输出可以通过管道做为另一个命令的输入，可以理解成是一个容器，存放在终端显示的内容。

**管道命令的效果图:**

![管道命令](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/%E7%AE%A1%E9%81%93%E5%91%BD%E4%BB%A4.png)

**说明:**

管道(|)一般结合 more 命令使用，主要是分配查看终端显示内容。

### 3. 小结

- 查看小文件使用 **cat** 命令
- 分屏查看大型文件使用 **more** 命令，
- 查看终端显示内容并分屏展示，使用 **管道(|)** 结合 **more** 命令。

## 三、链接命令

### 1.链接命令的介绍

链接命令是创建链接文件，链接文件分为：

01.软件链接：ln -s 

02.硬件链接: ln 

### 2.软连接

**软链接效果图:**

![软链接](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/%E8%BD%AF%E9%93%BE%E6%8E%A5-1.png)
![软链接](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/%E8%BD%AF%E9%93%BE%E6%8E%A5-2.png)
![软链接](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/%E8%BD%AF%E9%93%BE%E6%8E%A5-3.png)
![软链接](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/%E8%BD%AF%E9%93%BE%E6%8E%A5-4.png)
![软链接](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/%E8%BD%AF%E9%93%BE%E6%8E%A5-5.png)

**注意点:**

01.如果软链接跟源文件不在同一个目录，源文件要使用绝对路径，不能使用相对路径。

02.删除源文件则软链接失效

03.可以给目录创建链接

3.软链接小结：

01.软链接的作用是方便文件的快速访问，不如：给一个复杂的路径下的文件件创建一个软链接，以后就可以通过软链接完成快速访问操作。

02.创建软链接命令格式：ln -s源文件路径（使用绝对路径）软链接

### 4.硬链接

类似于原文件的一个别名，也就是说这两个名字指向的是同一个文件数据

![硬链接](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/%E7%A1%AC%E9%93%BE%E6%8E%A5-1.png)

**硬链接效果图:**

![硬链接](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/%E7%A1%AC%E9%93%BE%E6%8E%A5-2.png)
![硬链接](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/%E7%A1%AC%E9%93%BE%E6%8E%A5-3.png)
![硬链接](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/%E7%A1%AC%E9%93%BE%E6%8E%A5-4.png)
![硬链接](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/%E7%A1%AC%E9%93%BE%E6%8E%A5-5.png)
![硬链接](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/%E7%A1%AC%E9%93%BE%E6%8E%A5-6.png)
![硬链接](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/%E7%A1%AC%E9%93%BE%E6%8E%A5-7.png)
![硬链接](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/%E7%A1%AC%E9%93%BE%E6%8E%A5-8.png)

**注意点:**

01.创建硬链接使用相对路径和绝对路径都可以

02.删除源文件，硬链接还可以访问到数据。

03.创建硬链接，硬链接数会加1，删除源文件或者硬链接，硬链接数会减1

04.创建软链接硬链接数不会加1

05.不能给目录创建硬链接

### 5.硬链接小结

01.硬链接作用：给重要文件创建硬链接，能够防止文件数据被误删。

02.删除源文件，软链接失效，但是硬链接依然可以使用

03.创建硬链接命令格式：ln 源文件路径 硬链接

## 四、文本搜索命令

### 1.grep: 文本搜索

**grep命令效果图:**

![grep命令](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/grep.png)  

### 2.grep命令选项的使用

-i 忽略大小写

-n 显示匹配行号

-v 显示不包含匹配文本的所有行

**-i命令选项效果图:**

![grep命令选项](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/grep%E9%80%89%E9%A1%B9-1.png)  

**-n命令选项效果图:**

![grep命令选项](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/grep%E9%80%89%E9%A1%B9-2.png)  

**-v命令选项效果图:**

![grep命令选项](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/grep%E9%80%89%E9%A1%B9-3.png) 

### 3.grep命令结合正则表达式使用

1：^   以指定字符串开头

2：$   以指定字符串结尾

3：.    匹配一个非换行符的字符

**正则表达式‘^’的效果图:**

![grep正则](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/grep%E6%AD%A3%E5%88%99-1.png) 

**正则表达式‘$’的效果图:**

![grep正则](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/grep%E6%AD%A3%E5%88%99-2.png) 

**正则表达式‘.’的效果图:**

![grep正则](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/grep%E6%AD%A3%E5%88%99-3.png) 

### 4.扩展

01.grep命令还可以文本搜索管道中的内容，比如：ls/|grep'lib'

02.在使用grep命令的时候还可以省略搜索内容的引号，比如：ls / |grep lib ,grep hello1.txt

### 5.小结

01.grep命令是完成文本搜索操作的

02.文本搜索的命令格式：grep 选项 文本搜索内容

## 五、查找文件命令

### 1.find命令及选项的使用

find： 在指定目录下查找文件（包括目录） 格式: find 指定查找目录 -name "文件名"

**ind命令及选项的效果图:** 

![find命令及选项](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/find%E9%80%89%E9%A1%B9.png)

### 2. find命令结合通配符的使用

1. *：代表0个或者多个任意字符
2. ？：代表任意一个字符串

***通配符的效果图:**

![通配符](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/%E9%80%9A%E9%85%8D%E7%AC%A61.png)

**?通配符的效果图:**

![通配符](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/%E9%80%9A%E9%85%8D%E7%AC%A62.png)

**扩展:**

通配符不仅能结合 **find** 命令使用，还可以结合其它命令使用, 比如: **ls、mv、cp** 等，这里需要注意只有 **find** 命令使用通配符需要加上引号。

**扩展效果图:**

![find扩展](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/find%E6%89%A9%E5%B1%95.png)

### 3. 小结

- find命令是完成查找文件操作的
- 查找文件的命令格式: find 指定查找目录 -name "文件名"

## 六、压缩和解压缩命令

**学习目标**

- 能够使用tar命令完成文件的压缩和解压缩

------

### 1. 压缩格式的介绍

Linux默认支持的压缩格式:

- .gz
- .bz2
- .zip

**说明:**

- .gz和.bz2的压缩包需要使用tar命令来压缩和解压缩
- .zip的压缩包需要使用zip命令来压缩，使用unzip命令来解压缩

**压缩目的:**

- 节省磁盘空间

### 2. tar命令及选项的使用

| 命令 | 说明             |
| :--- | :--------------- |
| tar  | 压缩和解压缩命令 |

**tar命令选项:**

| 选项 | 说明                               |
| :--- | :--------------------------------- |
| -c   | 创建打包文件                       |
| -v   | 显示打包或者解包的详细信息         |
| -f   | 指定文件名称, 必须放到所有选项后面 |
| -z   | 压缩或解压缩(.gz)                  |
| -j   | 压缩或解压缩(.bz2)                 |
| -x   | 解包                               |
| -C   | 解压缩到指定目录                   |

**压缩成.gz的效果图:**

![tar命令](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/tar-1.png)  

**压缩成.bz2的效果图:**

![tar命令](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/tar-2.png) 

**解压缩.gz的效果图:**

![tar命令](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/tar-3.png) 

**解压缩.gz到指定目录效果图:**

![tar命令](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/tar-4.png) 

**解压缩.bz2的效果图:**

![tar命令](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/tar-5.png) 

**解压缩.bz2到指定目录效果图:**

![tar命令](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/tar-6.png) 

### 3. zip和unzip命令及选项的使用

| 命令  | 说明               |
| :---- | :----------------- |
| zip   | 压缩成.zip格式文件 |
| unzip | 解压缩.zip格式文件 |

**unzip命令选项:**

| 选项 | 说明             |
| :--- | :--------------- |
| -d   | 解压缩到指定目录 |

**压缩成.zip的效果图:**

![zip命令](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/zip-1.png)  

**解压缩.gz的效果图:**

![unzip命令](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/unzip-1.png) 

**解压缩.zip到指定目录效果图:**

![unzip命令](file:///F:/%E4%BC%A0%E6%99%BA%E6%92%AD%E5%AE%A2/%E5%B0%B1%E4%B8%9A%E7%8F%AD/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/unzip-2.png) 

**说明:**

1.压缩文件尽量使用gz格式，因为占用空间少

2.使用Zip命令压缩的文件占用空间比较多，当时比较通用，操作更加简单

### 4. 小结

1.gz和.bz2的压缩文件使用tar命令来完成压缩和解压缩

2..zip的压缩文件使用zip和unzip命令来完成压缩和解压缩

gzip 压缩

![1568252316241](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1568252316241.png)

![1568252428437](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1568252428437.png)



## 六、文件权限命令

### 1. chmod命令的介绍

| 命令  | 说明         |
| :---- | :----------- |
| chmod | 修改文件权限 |

chmod修改文件权限有两种方式:

- 字母法
- 数字法

### 2. chmod 字母法的使用

**角色说明:**

| 角色 | 说明                     |
| :--- | :----------------------- |
| u    | user, 表示该文件的所有者 |
| g    | group, 表示用户组        |
| o    | other, 表示其他用户      |
| a    | all, 表示所有用户        |

**权限设置说明:**

| 操作符 | 说明     |
| :----- | :------- |
| +      | 增加权限 |
| -      | 撤销权限 |
| =      | 设置权限 |

**权限说明:**

| 权限 | 说明       |
| :--- | :--------- |
| r    | 可读       |
| w    | 可写       |
| x    | 可执行     |
| -    | 无任何权限 |

**chmod命令字母法效果图:**

![chmod命令](file:///F:/%E5%B0%B1%E4%B8%9A%E7%8F%AD%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/chmod-1.png)

**chmod命令同时设置多个角色的效果图:**

![chmod命令](file:///F:/%E5%B0%B1%E4%B8%9A%E7%8F%AD%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/chmod-2.png)

### 3. chmod 数字法的使用

数字法就是“rwx” 这些权限也可以用**数字来代替**

**权限说明:**

| 权限 | 说明                  |
| :--- | :-------------------- |
| r    | 可读，权限值是4       |
| w    | 可写，权限值是2       |
| x    | 可执行，权限值是1     |
| -    | 无任何权限，权限值是0 |

**chmod命令数字法效果图:**

![chmod命令](file:///F:/%E5%B0%B1%E4%B8%9A%E7%8F%AD%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/chmod-3.png)

### 4. 小结

1.利用chmod命令可以控制文件的操作权限

2.字母法格式：chmod 不同角色设置的权限 文件

3.数字法格式：chmod 不同角色的权限值 文件名

## 七、获取管理员权限的相关命令

### 1. sudo命令的使用

| 命令    | 说明                                                       |
| :------ | :--------------------------------------------------------- |
| sudo -s | 切换到root用户，获取管理员权限                             |
| sudo    | 某个命令的执行需要获取管理员权限可以在执行命令前面加上sudo |

**sudo -s效果图:**

![sudo命令](file:///F:/%E5%B0%B1%E4%B8%9A%E7%8F%AD%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/sudo-1.png)

**sudo 命令效果图:**

![sudo命令](file:///F:/%E5%B0%B1%E4%B8%9A%E7%8F%AD%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/sudo-2.png)

**说明:**

1.如果只是某次操作需要使用管理员权限建议使用sudo,也就是说临时使用管理员权限

2.如果大量操作都需要使用管理员权限sudo -s,但是操作需谨慎

### 2. whoami命令的使用

| 命令   | 说明         |
| :----- | :----------- |
| whoami | 查看当前用户 |

**whoami 命令效果图:**

![whoami命令](file:///F:/%E5%B0%B1%E4%B8%9A%E7%8F%AD%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/whoami.png)

### 3. exit命令的使用

| 命令 | 说明         |
| :--- | :----------- |
| exit | 退出登录用户 |

**exit 命令的效果图:**

![exit命令](file:///F:/%E5%B0%B1%E4%B8%9A%E7%8F%AD%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/exit.png)

**说明:**

1.如果是切换后的登录用户，退出则返回上一个登录账号。

2.如果终端界面，退出终端

### 4. who命令的使用

| 命令 | 说明               |
| :--- | :----------------- |
| who  | 查看所有的登录用户 |

**who 命令的效果图:**

![who命令](file:///F:/%E5%B0%B1%E4%B8%9A%E7%8F%AD%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/who.png)

### 5. passwd命令的使用

| 命令   | 说明                                             |
| :----- | :----------------------------------------------- |
| passwd | 修改用户密码，不指定用户默认修改当前登录用户密码 |

**passwd 命令的效果图:**

![passwd命令](file:///F:/%E5%B0%B1%E4%B8%9A%E7%8F%AD%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/passwd.png)

### 6. which命令的使用

| 命令  | 说明         |
| :---- | :----------- |
| which | 查看命令位置 |

**which 命令的效果图:**

![which命令](file:///F:/%E5%B0%B1%E4%B8%9A%E7%8F%AD%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/which.png)

### 7. 关机和重启命令的使用

| 命令                                 | 说明     |
| :----------------------------------- | :------- |
| shutdown –h now（now也可以改成时间） | 立刻关机 |
| reboot                               | 重启     |

### 8. 小结

1.sudo是临时获取管理员权限

2.sudo -s是切换到管理员用户，一直使用管理员权限，谨慎操作

3.exit是退出当前用户

4.passwd 默认修改当前密码

5.在管理员用户下，passwd 用户名        修改其他用户密码

## 八、用户相关操作

### 1. 创建用户

| 命令    | 说明           |
| :------ | :------------- |
| useradd | 创建(添加)用户 |

**useradd命令选项:**

| 选项 | 说明                                                       |
| :--- | :--------------------------------------------------------- |
| -m   | 自动创建用户主目录,主目录的名字就是用户名                  |
| -g   | 指定用户所属的用户组，默认不指定会自动创建一个同名的用户组 |

**创建用户效果图:**

![useradd命令](file:///F:/%E5%B0%B1%E4%B8%9A%E7%8F%AD%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/useradd-1.png)

**查看所有用户信息的文件效果图:**

![useradd命令](file:///F:/%E5%B0%B1%E4%B8%9A%E7%8F%AD%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/useradd-2.png) ![useradd命令](file:///F:/%E5%B0%B1%E4%B8%9A%E7%8F%AD%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/useradd-3.png)

**说明:**

1.useradd命令的使用需要使用管理员权限，前面需要加上sudo

2.创建用户如果不指定用户，默认会自动创建一个同名的用户组

3.查看用户是否创建成功，可以查看/etc/passwd这个文件

4.查看用户组是否创建成功，可以查看/etc/group这个文件

注意：passwd文件中的每项信息说明,以root:x:0:0:root:/root:/bin/bash为例:

wuhao:x:1001:1000::/home/wuhao:

![1568271319713](F:\就业班上课资料\1568271319713.png)

- 第一个：用户名
- 第二个：密码占位符
- 第三个：uid, 用户id
- 第四个：gid, 用户所在组id
- 第五个：用户描述, 可选，
- 第六个：用户的主目录所在位置
- 第七个：用户所用 shell 的类型，一般由bash或者sh，默认不设置是sh类型

**group文件中的每项信息说明, 以laowang:x:1001:为例:**

- 第一个：用户组名
- 第二个：用户组密码占位符，一般Linux系统的用户组都没有密码的
- 第三个：组id

![1568271590104](F:\就业班上课资料\1568271590104.png)

 **id命令查看用户信息:** 

| 命令 | 说明         |
| :--- | :----------- |
| id   | 查看用户信息 |

 **id命令效果图:**   ![id命令](file:///F:/%E5%B0%B1%E4%B8%9A%E7%8F%AD%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/id.png)

 **每项信息说明:** 

uid=1001(laowang) gid=1001(laowang) 组=1001(laowang)

- 第一个: uid 表示用户id
- 第二个: gid 表示用户组id
- 第三个: 组 表示用户所在的用户组

### 2. 设置密码

给其它用户设置密码，需要使用: **sudo passwd 用户名**

 **设置密码效果图:**  ![useradd命令](file:///F:/%E5%B0%B1%E4%B8%9A%E7%8F%AD%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/%E8%AE%BE%E7%BD%AE%E6%96%B0%E7%94%A8%E6%88%B7%E5%AF%86%E7%A0%81.png)

### 3. 切换用户

| 命令 | 说明     |
| :--- | :------- |
| su   | 切换用户 |

**语法格式: su - 用户名**

 **切换用户效果图:** 

![su命令](file:///F:/%E5%B0%B1%E4%B8%9A%E7%8F%AD%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/su.png)

 **在laowang用户使用sudo -s效果图:** 

### 4. 删除用户

| 命令    | 说明     |
| :------ | :------- |
| userdel | 删除用户 |

 **userdel命令选项:** 

| 选项      | 说明                                               |
| :-------- | :------------------------------------------------- |
| -r 用户名 | 删除用户主目录，必须要设置，否则用户主目录不会删除 |

 **删除用户效果图:** 

![userdel命令](file:///F:/%E5%B0%B1%E4%B8%9A%E7%8F%AD%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/%E5%88%A0%E9%99%A4%E7%94%A8%E6%88%B7-1.png)

 **id查看用户信息效果图:** 

![userdel命令](file:///F:/%E5%B0%B1%E4%B8%9A%E7%8F%AD%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/%E5%88%A0%E9%99%A4%E7%94%A8%E6%88%B7-2.png)

 **查看group文件信息效果图:** 

![userdel命令](file:///F:/%E5%B0%B1%E4%B8%9A%E7%8F%AD%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/%E5%88%A0%E9%99%A4%E7%94%A8%E6%88%B7-3.png)

 **说明:** 

- 删除用户，默认同名的用户组也会被删除

### 5. 小结

1. 创建用户命令格式：sudo useradd -m 用户名，默认会创建 一个同名的用户组。
2. 产看用户信息使用id命令或者/etc/passwd文件
3. 给用户设置密码使用 sudo passwd 用户名
4. 切换用户使用 su - 用户名
5. 删除用户使用sudo userdel -r 用户名，默认会删除同名的用户组
6. 快捷键

alt + ctrl +f1 进入其他计算机用户登录界面

alt + ctrl + f7 退出其他组计算机用户，返回本用户

## 九、用户组相关操作

 **学习目标** 

- 能够知道创建用户组的命令

------

### 1. 创建用户组

| 命令     | 说明             |
| :------- | :--------------- |
| groupadd | 创建(添加)用户组 |

**创建用户组效果图:**

![groupadd命令](file:///F:/%E5%B0%B1%E4%B8%9A%E7%8F%AD%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/%E7%94%A8%E6%88%B7%E7%BB%84-1.png)

### 2. 创建用户并指定用户组

**创建用户并指定用户组效果图:**

![groupadd命令](file:///F:/%E5%B0%B1%E4%B8%9A%E7%8F%AD%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/%E7%94%A8%E6%88%B7%E7%BB%84-2.png)

### 3. 删除用户组

| 命令     | 说明       |
| :------- | :--------- |
| groupdel | 删除用户组 |

**删除用户组效果图:**

![groupdel命令](file:///F:/%E5%B0%B1%E4%B8%9A%E7%8F%AD%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/Python_Web%E5%9F%BA%E7%A1%805.2_html%E7%89%88/linux%E9%AB%98%E7%BA%A7%E5%91%BD%E4%BB%A4/imgs/%E7%94%A8%E6%88%B7%E7%BB%84-4.png)

**说明:**

- 如果用户组下面有用户先删除用户在删除用户组

### 4. 小结

- 创建用户组使用: **sudo groupadd 用户组名**
- 创建用户并指定用户组使用: **sudo useradd -m -g 用户组 用户名**
- 删除用户组使用: **sudo groupdel 用户组名**
- 查看用户组信息使用 **/etc/group文件**

![1568275719750](F:\就业班上课资料\1568275719750.png)