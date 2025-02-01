---
title: FuyuBot搭建
published: 2025-02-01
description: '教学搭建 FuyuBot 属于自己的聊天机器人'
image: ''
tags: [教学,随手记]
category: '教程分享'
draft: false 
lang: ''
---

# 介绍
[FuyuBot](https://github.com/CatMoeCircle/FuyuBot)是一个基于 [GramJS](https://github.com/gram-js/gramjs) 的 Telegram Bot 项目，支持用户自定义插件

# 开始
1. 克隆项目
```bash
git clone https://github.com/CatMoeCircle/FuyuBot.git
cd FuyuBot
```
2. 创建文件 `.env`

```bash
API_ID=123456  # Telegram API ID
API_HASH=123456789abcdefghijklmn # Telegram API Hash
BOT_TOKEN=123456:ABCDEFGHIJKLMNOPQRSTUVWXYZ # Telegram Bot Token
```
3. 安装依赖
```bash
apt update

apt install npm

npm install
```
4. 配置浏览器内核
```bash
dpkg --configure -a
sudo apt update
sudo apt install -y chromium-browser
```
5. 运行
```bash
npm test
```
6. 安装中文字体
```bash
sudo apt update
sudo apt install -y fonts-noto-cjk fonts-wqy-zenhei fonts-wqy-microhei
fc-cache -fv
sudo reboot
```


# 插件
安装插件也是非常方便，直接对着你bot发送
```bash
/plugins add 插件仓库
```
