## 基于TCP服务器的静态Web服务器_返回指定页面数据

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
            request_data = recv_data.split()
            request_path = request_data[1]
            if request_path.find('?') != -1:
                params = request_path.split('?')
                request_path = params[0]
            if request_path == '/':
                request_path = '/index.html'
            print('请求的路径是: %s' % request_path)


            try:
                with open('static' + request_path, 'rb') as file:
                    content = file.read()
            except Exception as e:
                response_line = 'HTTP/1.1 404 Not Found\r\n'
                response_head = 'Server: PWS/1.0\r\n'
                response_body = '<h1>Page Not Found !!!!</h1>'
                response_data = (response_line + response_head + '\r\n' + response_body).encode()
                client.send(response_data)

            else:

                response_line = 'HTTP/1.1 200 OK\r\n'

                response_head = 'Server: PWS/1.0\r\n'

                response_body = content

                response_data = (response_line + response_head + '\r\n').encode() + response_body

                client.send(response_data)
            finally:

                client.close()

```

3.设置启动

```python
def start(self):
        print('Serving ON 127.0.0.1:8888 .......')
        while True:
            client, ip_port = self.__server.accept()
            t = threading.Thread(target=self.__handle_task, args=(client,ip_port),daemon=True)
            t.start()
```

4.入口

```python
if __name__ == '__main__':
    server = SocketServer(8888)
    server.start()
```



```python
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

            # 分割请求报文,获取到请求资源路径,以备后面打开文件使用
            request_data = recv_data.split()

            # 获取请求资源路径
            request_path = request_data[1]
            # 因为请求资源可以会有参数,那么如果有参数就继续分割
            # /?name = user & passwd = 123
            if request_path.find('?') != -1:
                # 满足条件说明有参数,继续分割
                params = request_path.split('?')
                request_path = params[0]

            # 继续判断,如果请求的资源路径是 / 那么默认让服务器返回 首页
            if request_path == '/':
                request_path = '/index.html'

            print('请求的路径是: %s' % request_path)


            try:
                # 先读取文件
                with open('static' + request_path, 'rb') as file:
                    content = file.read()
            except Exception as e:
                # 有异常,可能访问的资源文件不存在

                response_line = 'HTTP/1.1 404 Not Found\r\n'
                response_head = 'Server: PWS/1.0\r\n'
                response_body = '<h1>Page Not Found !!!!</h1>'
                response_data = (response_line + response_head + '\r\n' + response_body).encode()
                client.send(response_data)

            else:
                # 正常打开文件,没有异常
                # 拼接响应报文,返回一个固定数据
                # 定义响应行
                response_line = 'HTTP/1.1 200 OK\r\n'

                # 定义一个响应头
                response_head = 'Server: PWS/1.0\r\n'

                # 定义一个响应体
                response_body = content

                # 拼接响应报文
                response_data = (response_line + response_head + '\r\n').encode() + response_body

                # 向客户端回传响应报文数据
                client.send(response_data)
            finally:
                # 关闭连接
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