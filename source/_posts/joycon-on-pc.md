---
title: Joy-Con on PC
date: 2022-05-03 21:11:18
tags:
- 资料整合
- 游戏
- 日常
---
## 缺个手柄。
封城封得头发昏，出不了小区门也就不想出家门。

偶然看到宝可梦初代的bug视频，于是就想（正常地）玩玩以前玩过的宝可梦（当时还没有这个官方译名）。

那么就找来模拟器和ROM开始游玩ルビサファ&エメラルド。游玩过程中发现，两只手被仅需的那几个键卡死在了键盘上，手臂很不舒服，得弄个手柄才行。但是我没PC用的手柄，由于封城快递也停了（倒不如说先阵亡的是快递）（倒不如说如果不封我也不会想玩宝可梦……）买也是不可能的。

没PC用的手柄，有Switch啊。本体的一对Joy-Con以及一个Pro Con都可以用作他用。（顺带一提有传言Switch将增加对GameBoy的支持，到时候有官方模拟器的话当然还是支持正版）

※本文不涉及技术研究和Coding。

<!-- more -->

## Pro Con
这东西就是个传统手柄。双摇杆、十字键、ABXY、LR/ZLZR、-+截图Home、振动、陀螺仪。

通过蓝牙连接PC后虽然不能直接被模拟器识别，但只要打开steam，就能识别Pro Con，并可以设置在游戏内的行为和在桌面下的行为。设置在桌面下的行为就可以映射到键盘进而映射到模拟器。由于宝可梦是不要求低延迟的RPG游戏，延迟感受不明显。

## Joy-Con
问题在于Joy-Con。网上关于Joy-Con在Windows下的使用五花八门，当然也是有很多人给它写了驱动的缘故。比较微妙的是，搜索结果中大多都指向把一对Joy-Con合成一个手柄来使用（合成后按键与Pro Con相当），而我只想要单个……。

毕竟GBA也就十字键、ABLR、Select/Start总共10个键，如果是DS，也就多了XY两个键，对于拥有摇杆、ABXY、SL/SR、L/ZL、－、截图键的单侧Joy-Con绰绰有余。虽然全用上姿势会很奇怪，但不是动作游戏就不要紧。

尝试了三种方案。

### 方案一：vJoy + JoyCon-Driver
这是最先找到的一个方案。文章点[这里](https://sspai.com/post/43982)。虽然这篇文章的目的是合成一个控制器，但发现JoyCon-Driver里有一个Combine JoyCons的选项，推测单侧Joy-Con也可以使用吧，就尝试了一下。

然后，JoyCon-Driver成功识别了JoyCon并给出了振动，其中迷之选项还能让陀螺仪映射到鼠标操作（都2202年了真的还会有人这么用吗……）

但是模拟器不认。这套方案的原理是JoyCon-Driver把Joy-Con的输入交给vJoy，vJoy作为一个虚拟手柄设备被Windows下的程序所识别。大概是中间哪个环节出了问题。

顺带一提按这篇文章的方案，要合成一个控制器的话还要再加一步驱动程序，真的需要那么复杂吗。

### 方案二：ViGEmBUS + xJoy
这是找到的第二个方案，视频见[这里](https://www.bilibili.com/video/BV12V411C71b/)。用到的两个软件都在GitHub上开源：[ViGEm/ViGEmBus](https://github.com/ViGEm/ViGEmBus) 和 [DuroSoft/XJoy](https://github.com/DuroSoft/XJoy)。

其实原理是一样的，两步走，驱动的驱动。

这次成了，模拟器能够正常识别输入。

但是。延迟。超级大。肉眼可见的那种大。也还是不能玩。

### 方案三：ViGEmBUS + BetterJoy
于是终于找到了能用的。至于哪篇文章介绍的找不到了。[Davidobot/BetterJoy](https://github.com/Davidobot/BetterJoy)

而且它拥有一个易用的图形界面。非常感谢。

![](https://user-images.githubusercontent.com/16619943/67919451-bf8e5680-fb76-11e9-995e-7193b87548e1.png)

它还提供了单个Joy-Con横置竖置的选项（对需要设置键位的模拟器来说其实没有区别，但竖置时SL/SR键被禁用，横置时L/ZL却能用，奇怪）。

感受不到什么延迟。设置好键位，就可以享受自由姿势的模拟器了。竖持Joy-Con玩RPG游戏，用上扳机键还挺爽的。

### 尾声
毕竟Joy-Con和Pro Con是给Switch设计的，在没有连接其他设备的情况下，只要插入Switch本体或是在手柄界面长按L+R即可轻松切换到Switch。要再连接电脑就得先把Switch的配对解除（或者休眠）再长按配对键连电脑，好不麻烦。

所以还是单独给PC配个手柄吧lol

其实整理这篇文的时候，笔者已经在eShop购买了船新宝可梦传说阿尔宙斯开始了新（旧？）时代的宝可梦之旅。

感谢您的阅读。




