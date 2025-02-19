---
title: FuyuBot搭建(环境篇)
published: 2025-02-19
description: '教学 FuyuBot 聊天机器人环境搭建'
image: ''
tags: [教学,随手记]
category: '教程分享'
draft: false 
lang: ''
---
# 介绍
[FuyuBot](https://github.com/CatMoeCircle/FuyuBot)是一个基于 [GramJS](https://github.com/gram-js/gramjs) 的 Telegram Bot 项目，支持用户自定义插件
## 搭建环境
- 服务器搭建
1. node安装
```bash
# 下载并安装 nvm:
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
# 替代重启 shell
\. "$HOME/.nvm/nvm.sh"
# 下载并安装 Node.js:
nvm install 22
# 验证 Node.js 版本:
node -v # 应该显示 "v22.14.0"
nvm current # 应该显示 "v22.14.0"
# 验证 npm 版本:
npm -v # 应该显示 "10.9.2"
```
2. 配置浏览器内核(根据网速判断，带宽小的服务器可能会导致长时间无响应，但是耐心等待即可)
```bash
sudo apt update
sudo apt install -y chromium-browser
```
3. git安装
```bash
sudo apt install -y git
```
4. 配置中文
```bash
sudo apt-get -y install fontconfig xfonts-utils
fc-list :lang=zh
sudo apt install fonts-noto-cjk
sudo apt install fontconfig
sudo dpkg-reconfigure fontconfig-config
sudo fc-cache -f -v
```
因为图像生成如果没中文会导致显示异常
- 安卓手机搭建
你可以使用一键脚本一键安装
```bash
bash <(curl -sL https://github.com/CatMoeCircle/FuyuBot/raw/main/scripts/termux.sh)
```
也可以在官方介绍找到对应文档[点击这里](https://github.com/CatMoeCircle/FuyuBot/blob/main/docs/README_zh-CN.md#termux)

- Windows搭建
你可以在文档的[点击这里](https://github.com/CatMoeCircle/FuyuBot/blob/main/docs/README_zh-CN.md#windows%E5%92%8Clinux)找到搭建教程

这就是本期的教程了