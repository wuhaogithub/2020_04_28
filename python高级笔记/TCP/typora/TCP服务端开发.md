## TCP服务端开发

1. 导入模块

   ```Python
   import socket
   ```

2. 创建服务端套接字对象

   ```Python
   server_socket = socket.socket()
   
   server_socket.setsockopt(socket.SOL_SOCKET,socket.SO_REUSEADDR,True)
   ```

   

3. 绑定端口号

   ```python
   server_socket.bind(('',8888))
   ```

   

4. 设置监听

   ```python
   server_socket.listen(128)
   ```

   

5. 等待接受客户端的连接请求

   ```python
   client_socket, ip_port = server_socket.accept()
   print('客户端 %s 使用 %s 端口连接成功....' % (ip_port[0], ip_port[1]))
   ```

   

6. 接收数据

   ```python
   recv_data = client_socket.recv(1024).decode()
   # 加个判断
   if len(recv_data) == 0:
       print('客户端 %s 下线了...' % ip_port[0])
   else:
       print('客户端 %s 使用 %s 端口发送来的数据是 %s ....' % (ip_port[0], ip_port[1], recv_data))
   ```
   

   
7. 发送数据

   ```python
   client_socket.send(recv_data.upper().encode())
   ```

   

8. 关闭套接字

   ```python
   client_socket.close()
   server_socket.close()
   ```

   

> ```python
> 
> '''
> TCP服务端开发
> '''
> # 0. 导入模块
> import socket
> 
> # 1. 创建服务端端套接字对象
> # server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
> server_socket = socket.socket()
> 
> # 1.1 端口复用,让程序在重启后,马上就能使用端口
> # setsockopt 方法用来设置 scoket选项
> # 参数一表示设置的是Socket选项
> # 参数二表示是重用地址和端口
> # 参数三表示是确定
> server_socket.setsockopt(socket.SOL_SOCKET,socket.SO_REUSEADDR,True)
> 
> # 2. 绑定端口号
> # 用来为服务器固定一个IP和端口,方便客户端访问
> # 参数也是一个元组
> # 参数如果是本机,可以直接写一个空引号,什么都不写,端口还得是数字类型
> server_socket.bind(('',8888))
> 
> # 3.设置监听
> # listten 方法用来设置最等待连接数,该方法一旦设置后,这个socket对象就变成了一个只能被动接收请求的对象
> # 不能主动进行收发数据
> # 参数的128表示该对象最多可以有128个连接去等待
> server_socket.listen(128)
> 
> # 4.等待接受客户端的连接请求
> # 该方法返回一个元组,包含了连接上来的客户端对象,和客户端对象的IP地址信息
> client_socket, ip_port = server_socket.accept()
> print('客户端 %s 使用 %s 端口连接成功....' % (ip_port[0], ip_port[1]))
> # 接收数据
> # 接收数据时,要使用连接上来的客户端socket进行接收
> recv_data = client_socket.recv(1024).decode()
> 
> # 加个判断
> if len(recv_data) == 0:
>     print('客户端 %s 下线了...' % ip_port[0])
> else:
>     print('客户端 %s 使用 %s 端口发送来的数据是 %s ....' % (ip_port[0], ip_port[1], recv_data))
> 
> # 5.发送数据
> # 发送数据时,也是利用客户端的socket来为客户端发送数据
> # client_socket.send('你好也...'.encode())
> 
> # 练习,小需求:将客户端发送的字母转大写返回
> client_socket.send(recv_data.upper().encode())
> 
> 
> # 关闭套接字
> client_socket.close()
> server_socket.close()
> ```
>

