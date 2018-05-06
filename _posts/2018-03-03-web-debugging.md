---
layout: post
title: Chrome Web调试方法
description: 
category: blog
---


调试快捷键：F12

Dock side : 调试窗口位置，全屏、左侧、下方、右侧

Toggle XXX ： 移动设备端调试，可以修改手机型号、屏幕大小尺寸进行调试，圆圈模拟手势操作

### Elements 
DOM信息 ，渲染出的所有元素
- Styles: 样式信息，有下划线表示被覆盖的CSS样式，可以直接修改CSS样式信息用做调试，如背景色之类的
- Computed: 盒子模型，可以修改边距等信息，用做调试
- Event Listeners: 事件监听

### Console
控制台，代码中的日志信息均在这里打印，也可以输入一些函数进行测试

### Source
源码，用于调试问题。
如：
- 打开一个js文件
- 左下角'{}'展开文件
- 在展开的js文件中添加断点，刷新页面进行调试
- 在堆栈信息中查找其被调用的情况，上面的栈是被调用的，下面的栈是调用的信息

### Network
网络传输信息
- Filter 过滤 
- All 显示所有信息

#### Headers
- General  
```
    Request URL: 请求的URL地址， https://域名/位置

    Request Method: 请求方式 Get Post 等

    Status Code: 200 状态

    Remote Address: DNS解析域名的IP地址 + 端口号

    Referrer Policy: 
```
- Response Headers
```
    cache-control: private

    略
```
- Request Headers
```
    :method: GET 请求方式

    :path: 访问路径

    :scheme: https 协议

    accept: application/json, text/javascript 接受类型 q: 权重

    accept-encoding: gzip, deflate, br 通知服务端用什么方式压缩。

    说明：由于传输的文件可能很大，需要在服务端进行压缩，传输到客户端后再进行解压，压缩/解压的方式

    accept-language: 语言

    cookie: cookie信息，包含浏览器和服务端的cookie信息

    referer: 源地址
```
- Query String Parameters

#### Preview
格式化展示服务端返回的信息

#### Response
服务端返回的信息，可以拷贝出来

#### Cookies 
可以查看Cookies信息

#### Timing
耗时信息，用于查看 服务端响应时间、下载资源时间等。

Resource Scheduling： 排队时间  
Connection Start Stalled: 大多数是网络问题，也有可能是浏览器问题  
Request/Response:   
Request sent Waiting: 服务端响应时间  
Content Download: 获取服务端资源时间

### Memory 
性能优化时使用

### Application 
Storage 
- Local Storage: 存储在本地，大小有限制，会话结束还存在
- Session Storage: 存储在会话，会话结束即清空
- Cookies：可以删除、修改Cookies信息

### HTTP状态
- 1XX ：消息，表示请求已被接受，需要继续处理
- 2XX ：成功，表示请求已成功被服务器接收、理解并处理
- 3XX ：重定向，表示请求已被处理单需要客户端采取进一步的操作才能完成请求
- 4XX : 请求错误，表示客户端可能发生了错误，妨碍了服务器的处理
- 5XX ：服务器错误，表示服务器在处理请求的过程中有错误或异常状态发生，或其他原因导致无法完成对请求的处理
- 6XX ：同5XX

### Cookies 
e : 浏览器  
s : 服务端，Tomcat \ Apptch \ node \ nginx等
```
    e -> s, 不包含cookies信息
    s -> e, 包含服务端返回的cookies信息，传输至 e
    e -> s, 包含之前s返回的cookies信息+e自己生成的某些cookies信息
```







