# h5-doc
h5调试相关文档
具体记录了一下h5各种调试的方法
1 概述
H5主要分为两种：一种是嵌入应用内部的页面，通常依赖指定的客户端，统称webview；另一种是用户直接通过浏览器访问，统称外链H5通常不依赖特定的客户端。两种H5的形式不冲突，可以做兼容。

2 调试

    利用同域原理调试h5.测试网络是否有权限，可以运行一个本地项目，打开浏览器，访问运行本地的ip+port，能访问通网络就通，访问不了，就是网络不通
看ui效果，只需要在真机的浏览器上运行本地的IP+port，但是如果是功能的调试，就要走另一个步骤。
b. 使用adb调试
 安卓调试桥Android Debug Bridge,是一个android 的调试工具
将手机设置成开发者模式，并勾选同意usb调试；
用usb连接电脑，并选择传输文件模式；
确认客户端提供的测试包添加了调试命令：WebView.setWebContentsDebuggingEnabled(true);
在终端进入adb工具包的位置（或者配置成电脑的全局变量，每次就可以直接输入命令），执行adb devices 命令，查看手机的连接情况，连接正常会出现一个 list显示电脑连接的手机数；
图片: https://odocs.myoas.com/uploader/f/rnA6FkCQIUgQHE6e.png?accessToken=eyJhbGciOiJIUzI1NiIsImtpZCI6ImRlZmF1bHQiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOiJhY2Nlc3NfcmVzb3VyY2UiLCJleHAiOjE2MzYwOTgyNzMsImciOiI4Tms2TXdyNjBFSHlSVnFMIiwiaWF0IjoxNjM2MDk4MjQzLCJ1c2VySWQiOjcyOTQ5fQ.scH06L5UdXjjNHAgG69ldKKGOKjyGVk4YT6rxtATQnc
在谷歌上打开chrome://inspect/#devices，正常情况就会检测出可以调试的h5项目，然后进入自己的h5页面，就可以调试了；
如果没有出现，请确认网络是否互通，测试包是否添加了调试命令，或者使用的usb能否调试（多头的usb有可能无法调试）

附件: adb-tools.zip https://odocs.myoas.com/uploader/f/S3yvUMj5zhJqjqYC.zip?accessToken=eyJhbGciOiJIUzI1NiIsImtpZCI6ImRlZmF1bHQiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOiJhY2Nlc3NfcmVzb3VyY2UiLCJleHAiOjE2MzYwOTgyNzMsImciOiI4Tms2TXdyNjBFSHlSVnFMIiwiaWF0IjoxNjM2MDk4MjQzLCJ1c2VySWQiOjcyOTQ5fQ.scH06L5UdXjjNHAgG69ldKKGOKjyGVk4YT6rxtATQnc
adb其他相关知识点可参考：https://developer.android.google.cn/studio/command-line/adb?hl=zh-cn

3 微信QQ调试方法
使用VConsole

4 日志
*#800#--其他--屏幕录制按钮可打开录屏--开始抓取--去应用操作--结束后返回抓取日志界面选：完成并反馈--链接电脑--.Android >data 
一般结束后会弹出一个日志文件存储的地址，直接去找就行
