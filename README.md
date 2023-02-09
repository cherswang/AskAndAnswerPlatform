# AskAndAnswerPlatform
小型的在线提问平台

这是给小白入门H5和Nodejs参考的一个小型完整项目，包含前端和服务器的实现，主要提供了登录、注册、查看列表、提问、回答这几个功能，分别对应的有自己的页面和事件脚本。页面布局以bootstrap为基础框架，页面请求采用ajax的方式，比较传统老旧，但是功能健全。后端服务器使用node.js去实现，核心代码都在server.js文件中。

使用过程中面临的Mac终端命令列举如下：
1、启动服务器，cd到server.js所在的目录，执行node server.js
2、关闭服务器，ctrl+c，这种方式能直接杀死进程，端口号也会被释放出来

前端如何访问：
用户终端机直接在浏览器地址栏输入服务器的IP地址和服务端口，就可以访问这个在线平台。

备注：
一、假如关闭服务器了，但是端口号被占用的时候，可以尝试如下操作步骤
1、查看端口号（以port：3000为例子）
终端输入为：sudo lsof -nP | grep LISTEN | grep  3000
终端输出为：node      4041               wanggang   22u     IPv6 0xd07f8e1484a20b2d         0t0                 TCP *:3000 (LISTEN)

上面的node为进程名称，4041即为在活动监视器中的PID，去Mac活动监视器中找到对应的进程，强制关闭就可以了。

二、本机启动服务器之后，想用其他客户端登录使用这个服务，需要知道服务的地址，此时需要查看本机地址
1、查看本机IP地址
终端输入为：ifconfig en0
终端输出为：en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	options=400<CHANNEL_IO>
	ether 3c:06:30:50:54:b2 
	inet6 fe80::1caa:dc93:8e49:bb47%en0 prefixlen 64 secured scopeid 0xc 
	inet 192.168.31.105 netmask 0xffffff00 broadcast 192.168.31.255
	nd6 options=201<PERFORMNUD,DAD>
	media: autoselect
	status: active

2、 也可以使用这个命令查询本机IP
终端输入为：ifconfig | grep "inet " | grep -v 127.0.0.1
终端输出为：inet 127.0.0.1 netmask 0xff000000 
	inet 192.168.31.105 netmask 0xffffff00 broadcast 192.168.31.255
