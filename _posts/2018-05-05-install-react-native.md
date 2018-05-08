---
layout: post
title: 安装React Native
description: 搭建移动端开发环境
category: blog
---

### 步骤
+ 打开[官网](https://reactnative.cn/)
+ 安装Python 2，打开Python官网下载安装版本为2的Python；
+ 安装Node.js，打开Node官网下载安装；
+ 设置npm镜像，指向淘宝；    
`npm config set registry https://registry.npm.taobao.org --global`     
`npm config set disturl https://npm.taobao.org/dist --global`
+ 安装React Native的命令行工具    
`npm install -g react-native-cli`
+ 安装Java Development Kit [JDK] 1.8
+ 安装Android Studio
  + 点击安装，直至进入Install Type界面，点击Cancel
  + 进入Android Studio界面时，打开Configure -> SDK Manager界面
  + 可以修改Android SDK Location地址     
  说明：Android SDK Location地址默认在C:\Users\用户名\AppData\Local\Android\Sdk目录下
  + SDK Platforms下，选择Show Package Details，然后在Android 6.0中勾选Android SDK Platform 23
  + SDK Tools下，选择Show Package Details，然后在Android SDK Build Tools中勾选Android SDK Build-Tools 23.0.1（至少），还要勾选Android Support Repository
  + 安装直至完成

+ 设置环境变量
  + 右键 计算机 -> 属性 -> 高级系统设置 -> 高级 -> 环境变量 
  + 新建 变量名ANDROID_HOME,变量值为Android SDK Location地址的项
  + 选中PATH -> 将Android SDK的tools和platform-tools目录添加到PATH变量中     
  注意：PATH路径以 ; 分隔

+ 下载并安装git for windows     
  注意：安装过程中注意选中"Run Git from Windows Command Prompt"

### 测试安装
+ 设置工作目录，运行 `react-native init MyProject`
+ 工作目录下，运行 `react-native start`
+ 浏览器访问 http://localhost:8081/index.bundle?platform=android，能看到很长的js代码
+ 电脑连接手机，打开开发者模式，允许手机进行调试
+ 工作目录下，运行 `react-native run-android`，运行完成后能在手机上看到App运行，并显示     
  `Welcome to React Native!`     
  `To get started, edit App.js`     
  `Double tap R on your keyboard to reload,`     
  `Shake or press menu button for dev menu`     
  说明环境搭建好了。
