---
title: screen
published: 2024-12-16
description: 'screen 命令使用'
image: './img/2.png'
tags: [Linux , 命令]
category: '教程分享'
draft: false 
lang: ''
---

# screen的功能

- 会话恢复
- 多窗口
- 会话共享

# 安装

``` bash
# CentOS
yum install screen
# Debian/Ubuntu
apt install screen
```

# 命令查看

``` bash
screen -help
```

1.终端列表

``` bash
screen -ls
```

2.新建终端
``` bash
screen -S 终端名称
```

3.退出当前终端(保持后台运行)

我们按`Ctril+a`再按`d`

4.回到终端

``` bash
screen -r 终端的PID或者name
```
5. 杀掉指定终端会话  

如果需要结束某个后台运行的 `screen` 会话，可以使用以下命令：  

```bash
screen -X -S 终端名称(或PID) quit
```  

6. 分屏操作  

`screen` 支持在同一个会话中分割屏幕以便同时查看多个窗口：  

- **水平分屏**：  
  按下 `Ctrl+a`，然后按 `S`  

- **垂直分屏**：  
  按下 `Ctrl+a`，然后按 `|` (部分键盘可能需要先按 `Shift+\` 来输入竖线)  

- **切换光标到另一屏幕**：  
  按下 `Ctrl+a`，然后按 `Tab`  

- **关闭当前分屏**：  
  按下 `Ctrl+a`，然后按 `X`  

7. 保存屏幕日志  

可以记录当前 `screen` 会话的所有输出：  

```bash
Ctrl+a :logfile 文件名
Ctrl+a :log on
```  

要停止日志记录：  

```bash
Ctrl+a :log off
```  

8. 自定义 `screen` 配置  

`screen` 支持通过配置文件 `.screenrc` 自定义快捷键和行为。配置文件通常存放在用户的主目录下，示例如下：  

```bash
# 开启时自动显示屏幕列表
startup_message off
# 设置默认窗口名称
shelltitle "$ |bash"
# 映射快捷键（示例为绑定 F9 键到分屏功能）
bindkey -k k9 split
```  

编辑后，重新启动 `screen` 即可生效。