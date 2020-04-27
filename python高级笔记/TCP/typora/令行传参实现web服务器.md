令行传参实现web服务器

```python
import socket
import threading
import sys
class SocketServer(object):
    def __init__(self, port):
        self.__server = socket.socket()
        self.__server.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, True)
        self.__server.bind(('', port))
        self.__server.listen(128)
    def __handle_task(self, client, ip_poirt):
        print('客户端 %s 使用 %s 端口连接成功....' % (ip_poirt[0], ip_poirt[1]))
        recv_date = client.recv(1024).decode()
        print(recv_date)
        if len(recv_date) == 0:
            print('客户端 %s 下线了....' % ip_poirt[0])
        else:
            request_data = recv_date.split()
            request_path = request_data[1]
            if request_path.find('?') != -1:
                params = request_path.split('?')
                request_path = params[0]
            if request_path == '/':
                request_path = '/index.html'
            print('请求的路径是： %s' % request_path)
            try:
                with open('static' + request_path,'rb') as file:
                    content = file.read()
            except Exception as e:
                response_line = 'HTTP/1.1 404 Not Found\r\n'
                response_head = 'Server: PWS/1.0\r\n'
                response_body = '<h1>Page Not Fount!!!</h1>'
                request_data = (response_line + response_head + '\r\n' + response_body)
                client.send(request_data)
            else:
                response_line = 'HTTP/1.1 200 OK\r\n'
                response_head = 'Server: PWS/1.0\r\n'
                response_body = content
                response_data = (response_line + response_head + '\r\n').encode() + response_body
                client.send(response_data)
            finally:
                client.close()
    def start(self):
        print('Serving ON 127.0.0.1:%s .......' % port)
        while True:
            client, ip_port = self.__server.accept()
            t = threading.Thread(target=self.__handle_task, args=(client, ip_port), daemon=True)
            t.start()
if __name__ == '__main__':
    print('请以以下方式启动服务器： python3 xxx.py 8000')
    if len(sys.argv) != 2:
        print('启动参数错误，请重新启动...')
    else:
        port = sys.argv[1]
        if port.isdigit():
            port = int(port)
            server = SocketServer(port)
            server.start()
        else:
            print('端口不是数字')
```



```python
import socket
import threading
import sys
class SocketServer(object):
    def __init__(self, port):
        self.__server = socket.socket()
        self.__server.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, True)
        self.__server.bind(('', port))
        self.__server.listen(128)
    def __handle_task(self, client, ip_poirt):
        print('客户端 %s 使用 %s 端口连接成功....' % (ip_poirt[0], ip_poirt[1]))
        recv_date = client.recv(1024).decode()
        print(recv_date)
        if len(recv_date) == 0:
            print('客户端 %s 下线了....' % ip_poirt[0])
            # 分割请求报文，获取到请求资源，以备后面打开文件使用
        else:
            request_data = recv_date.split()
            #获取请求资源路径
            request_path = request_data[1]
            # 因为请求资源可能会有参数，那么如果有参数就继续分割
            # /?name = user & passwd = 123
            if request_path.find('?') != -1:
                # 满足条件说明有参数，继续分割
                params = request_path.split('?')
                request_path = params[0]
            #  继续判断，如果请求的资源路径是 / 那么默认让服务器返回 首页
            if request_path == '/':
                request_path = '/index.html'
            print('请求的路径是： %s' % request_path)
            try:
                with open('static' + request_path,'rb') as file:
                    content = file.read()
            except Exception as e:
                response_line = 'HTTP/1.1 404 Not Found\r\n'
                response_head = 'Server: PWS/1.0\r\n'
                response_body = '<h1>Page Not Fount!!!</h1>'
                request_data = (response_line + response_head + '\r\n' + response_body)
                client.send(request_data)
            else:

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
                client.close()

            # 启动方法
    def start(self):
        # 输出提示信息
        print('Serving ON 127.0.0.1:%s .......' % port)

        # 让服务器死循环接收客户端的请求
        while True:
            # 接收请求
            client, ip_port = self.__server.accept()

            # 实现一个子线程对象,让他去一边去处理客户端的接收数据请求
            t = threading.Thread(target=self.__handle_task, args=(client, ip_port), daemon=True)
            t.start()

                    # self.__server.close()

# 入口
if __name__ == '__main__':
    print('请以以下方式启动服务器： python3 xxx.py 8000')
    if len(sys.argv) != 2:
        print('启动参数错误，请重新启动...')
    else:
        port = sys.argv[1]
        if port.isdigit():
            port = int(port)

            # 创建一个多任务的socket服务器对象
            server = SocketServer(port)
            # 并且启动
            server.start()
        else:
            print('端口不是数字')


```

