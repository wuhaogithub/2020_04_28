## TCP客户端开发

1. 导入模块

   ```python
   import socket
   ```

2. 创建客户端套接字对象

   ```python
   client_socket = socket.socket(socket.Af_INET, socket.SOCK_STREAM)
   ```

3. 和服务端套接字建立连接

   ```python
   client_socket.connect(('192.168.36.31',9999))
   ```

4. 发送数据

   ```python
   send_date = 'hellp world'
   client_socket.send(send_date.encode('utf-8'))
   ```

5. 接收数据

   ```python
   recv_date = client_socket.recv(1024)
   print(recv_date.decode('utf-8'))
   ```
   
6. 关闭客户端套接字

   ```python
   client_socket.close()
   ```

   ```python
   '''
   P01_TCP客户端开发
   '''
   
   # 0. 导入模块
   import socket
   
   # 1. 创建客户端套接字对象
   # 参数一表示是建立Socket时,使用的IP类型
   # AF_INET 表示使用 ipv4
   # AF_INET6 表示使用 IPv6 (了解)
   # 参数二表示的是建立Socket时,使用的通信协议类型
   # SOCK_STREAM 表示使用是 TCP 协议
   # SOCK_DGRAM  表示使用的是 UDP 协议(了解)
   client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
   # 如果建立的是TCP方式的socket可以不传任何参数,直接创建即可
   # client_socket = socket.socket()
   
   # 2. 和服务端套接字建立连接
   # connect 函数用来连接服务器,传入的参数是一个元组,要包含 IP和端口两项
   # IP要使用字符串,端口使用数字
   
   client_socket.connect(('192.168.36.47',9999))
   # 3. 发送数据
   # 因为socket是以TCP方式连接的,所以所有收发的数据都是二进制的,所以要对发送的数据进行编码或解码
   data = 'Hello, 你好'
   # TypeError: a bytes-like object is required, not 'str'
   # 发送的数据必须 是二进制,不能是普通 的字符串
   client_socket.send(data.encode('utf-8'))
   
   # 4. 接收数据
   
   recv_data = client_socket.recv(1024)
   print(recv_data)
   # 因为收到的数据也是二进制,所以也需进行解码
   print(recv_data.decode('utf-8'))
   
   # 5. 关闭客户端套接字
   client_socket.close()
   ```
   
   