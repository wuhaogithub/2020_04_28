## 基于TCP服务器的静态Web服务器_返回固定页面数据

1.导入模块

```python
import socket
import threading
```

2.实现这个类

```python
class SocketServer(object):
    def __init__(self,port):
        self.__server = socket.socket()
        self.__server.setsockopt(socket.SOL_SOCKET,socket.SO_REUSEADDR,True)
        self.__server.bind(('',port))
        self.__server.listen(128)
    def __handle_task(self,client, ip_port):
        print('客户端 %s 使用 %s 端口连接成功....' % (ip_port[0], ip_port[1]))
        recv_data = client.recv(1024).decode()
        print(recv_data)
        if len(recv_data) == 0:
            print('客户端 %s 下线了....' % ip_port[0])
        else:
            response_line = 'HTTP/1.1 200 OK\r\n'

            response_head = 'Server: PWS/1.0\r\n'

            with open('static/index.html','r') as file:
                content = file.read()
            response_body = content
            response_data = (response_line + response_head + '\r\n' + response_body).encode()
            client.send(response_data)
            client.close()
```

3.启动方法

```python
def start(self):
        # 输出提示信息
        print('Serving ON 127.0.0.1:8888 .......')

        # 让服务器死循环接收客户端的请求
        while True:
            # 接收请求
            client, ip_port = self.__server.accept()
            # 实现一个子线程对象,让他去一边去处理客户端的接收数据请求
            t = threading.Thread(target=self.__handle_task, args=(client,ip_port),daemon=True)
            t.start()
```

4.入口

```python
if __name__ == '__main__':
    # 创建一个多任务的socket服务器对象
    server = SocketServer(8888)
    # 并且启动
    server.start()
```



```python
'''
P04_基于TCP服务器的静态Web服务器_返回固定页面数据.py
'''

# 导入模块
import socket
import threading


# 实现这个类
class SocketServer(object):
    # 实现初始化方法,在实现这个对象时,就将Socket的准备工作做好
    def __init__(self,port):
        self.__server = socket.socket()
        self.__server.setsockopt(socket.SOL_SOCKET,socket.SO_REUSEADDR,True)
        self.__server.bind(('',port))
        self.__server.listen(128)


    # 实现一个子线程的任务函数,参数接收客户端对象和信息
    def __handle_task(self,client, ip_port):
        print('客户端 %s 使用 %s 端口连接成功....' % (ip_port[0], ip_port[1]))

        # 接收数据
        recv_data = client.recv(1024).decode()
        # 输出浏览器发过来的请求报文
        print(recv_data)

        # 判断
        if len(recv_data) == 0:
            print('客户端 %s 下线了....' % ip_port[0])

        else:
            # 拼接响应报文,返回一个固定数据
            # 定义响应行
            response_line = 'HTTP/1.1 200 OK\r\n'

            # 定义一个响应头
            response_head = 'Server: PWS/1.0\r\n'


            # 先读取文件
            with open('static/index.html','r') as file:
                content = file.read()


            # 定义一个响应体
            response_body = content

            # 拼接响应报文
            response_data = (response_line + response_head + '\r\n' + response_body).encode()

            # 向客户端回传响应报文数据
            client.send(response_data)


            client.close()


    # 启动方法
    def start(self):
        # 输出提示信息
        print('Serving ON 127.0.0.1:8888 .......')

        # 让服务器死循环接收客户端的请求
        while True:
            # 接收请求
            client, ip_port = self.__server.accept()

            # 实现一个子线程对象,让他去一边去处理客户端的接收数据请求
            t = threading.Thread(target=self.__handle_task, args=(client,ip_port),daemon=True)
            t.start()

        # self.__server.close()



# 入口
if __name__ == '__main__':
    # 创建一个多任务的socket服务器对象
    server = SocketServer(8888)
    # 并且启动
    server.start()
```

