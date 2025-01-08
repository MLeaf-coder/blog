---
title: docker-qemu-arm
published: 2025-01-09
description: 'termux安装Docker x86_64'
image: ''
tags: [docker, termux]
category: 安卓折腾记
draft: false 
lang: ''
---
# 前言
时隔几个月我又来折腾这个termux运行Docker这个项目了，那么我们废话不多说开搞

# 介绍
本期使用到的项目为

::github{repo="egandro/docker-qemu-arm"}

也是在不断折腾下看到了这给项目

当然还有[参考项目](https://gist.github.com/oofnikj/e79aef095cd08756f7f26ed244355d62)

# 开始

首先来到项目可以看到这个项目给出了一个自动脚本
```bash
bash -c "$(curl -fsSL https://raw.githubusercontent.com/egandro/docker-qemu-arm/master/termux-setup.sh)"
```

当然也有半自动
```bash
pkg update
pkg install git
git clone https://github.com/egandro/docker-qemu-arm.git
cd docker-qemu-arm
cp config.sample config.env
# vi config.env # change everything you want to need to change
./install.sh
```

启动命令
```bash
$HOME/alpine
./startqemu.sh
```

# 已知问题

- 仅Alpine Linux和dns和ipv4与ipv4/6相比（经常）出问题
- 我们将 dns 固定到（可以更改），在 Alpine 中我们关闭 ipv6 8.8.8.8

# 建议

带点科学工具不然下载不到某些东西

# 总结

我没研究太仔细，启动时报错图片丢失

(⊙_☉)
