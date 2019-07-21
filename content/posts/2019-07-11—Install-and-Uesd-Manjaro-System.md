---
title: "manjaro 系统安装"
date: "2019-07-10T22:40:32.169Z"
template: "post"
draft: false
slug: "/posts/安装manjaro系统/"
category: "系统"
tags:
  - "linux"
  - "manjaro"
  - "kde"
  - "system"
description: "初步介绍 manjaro 系统"
---

### 制作U盘启动

1: 先去[官网](https://manjaro.org/download/)下载最新版本`manjaro`系统

2: 下载[rufus](https://rufus.ie/zh_CN.html), `rufus` 是一个是一个可以帮助格式化和创建可引导USB闪存盘的工具

3: 准备一个u盘

现在可以开始制作Manjaro系统安装盘了。 打开rufus， 按照下图设置：

![](https://aitting.cn/blog/6dt1y.jpg)

![](https://aitting.cn/blog/gj7kf.jpg)
**Note: 选择DD模式写入，ios模式写入的启动不了**

### 安装步骤

1. 设置bios，关闭安全启动， 进入启动选项界面，选择uefi usb启动项.（ps: 不同的电脑， 进入bios的指令不同，可以非常容易的在网上查到。笔者的电脑关闭安全启动/设置启动项分别对应的是F10/F9）

2. 设置完成U盘启动之后， 电脑会进入一个临时页面（下图）
   ![](https://aitting.cn/blog/y72r4.jpg)
   
3. 双击 `Boot: Manjaro.x86._64 xfce` 进入安装页面。如下图， 选择中文， 点击启动安装程序
   ![](https://aitting.cn/blog/bs4cf.jpg)
   
4. 安装步骤
   1. 欢迎界面， 可以选择语言
      ![](https://aitting.cn/blog/myhtw.jpg)
   2. 位置， 默认好像就是上海， 如果不是话，手动选择为上海
      ![](https://aitting.cn/blog/6pnxv.jpg)
   3. 键盘的话， 就选择`chinese  default`
      ![](https://aitting.cn/blog/s4rg7.jpg)
   4. 分区（重点）
      分区有3种选择：清除磁盘、 默认安装、和手动分区,　我们这个选择的是手动分区,  具体信息如下
   5. 分区完成之后，　就可额可以安装了，　等待10~20分钟就可以了
      NOTE:　按照在94％左右的时候会提示`update configure`之类的，系统会卡住，　国内的话你断开网络链接就可以了，　稍微等待一下安装完成．
   
   ### 必要软件安装
   
   
   
   

