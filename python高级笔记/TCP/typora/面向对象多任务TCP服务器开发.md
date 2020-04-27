## 面向对象多任务TCP服务器开发

1.导入模块

```pytho
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
        if len(recv_data) == 0:
            print('客户端 %s 下线了....' % ip_port[0])
        else:           
            client.send(recv_data.upper().encode())
            client.close()
```

3.启动方法

```python
def start(self):        
        while True:           
            client, ip_port = self.__server.accept()            
            t = threading.Thread(target=self.__handle_task, args=(client,ip_port),daemon=True)
            t.start()
        # self.__server.close()
```

4.创建线程入口

```python
if __name__ == '__main__':    
    server = SocketServer(8888)   
    server.start()
```



```python
'''
P03_面向对象多任务TCP服务器开发
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

        # 判断
        if len(recv_data) == 0:
            print('客户端 %s 下线了....' % ip_port[0])

        else:
            # 接收发送数据
            client.send(recv_data.upper().encode())
            client.close()


    # 启动方法
    def start(self):
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

