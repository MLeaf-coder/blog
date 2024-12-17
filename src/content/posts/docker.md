---
title: 安装docker
published: 2024-10-21
image: 'https://github.com/FY-yun/picx-images-hosting/raw/master/20241217/docker.6ikclxtv5n.webp'
description: 安卓termux安装docker
tags: [docker, termux]
category: 安卓折腾记
draft: false
---

# 前言

本期教程很干货，要是没有动手能力建议不要尝试安装思路如下

```flow
process=>operation: termux
e=>end: QEMU
b=>end: Alpine Linux
start=>start: docker

process->e->b->start
```

我们需要在 termux 安装 QEMU 模拟器再安装 Alpine Linux 最后在安装 docker

:::note
简称——无限套娃，因为没有 root 和安卓本身的功能缺失只能这样
:::

# QEMU 是什么

什么是 QEMU
QEMU 是一种通用的开源计算机仿真器和虚拟器。QEMU 共有两种操作模式

全系统仿真：能够在任意支持的架构上为任何机器运行一个完整的操作系统

用户模式仿真：能够在任意支持的架构上为另一个 Linux/BSD 运行程序

# Alpine Linux 是什么

alpine 是一个轻量级的 Linux 发行版本，轻量级不仅体现在其占用空间的大小，还因为他没有图形化界面，只有命令行界面。 这个发行版本与我们常见的发现版本不同，其他版版本基本在安装完基本配置之后就可以使用了，而且基本配置如：磁盘，时区等都可以通过图形化的方式去点击进行配置，alpine 需要我们在命令行进行手动配置

# 安装准备工作

1. 安装 termux

2. 打开 termux 然后安装 wget

```bash
pkg install wget
```

3. 安装 qemu

```bash
pkg install qemu-system-x86-64-headless qemu-utils
```

4. 使用 wget 下载 Alpine Linux 文件 iso 文件

```bash
wget https://dl-cdn.alpinelinux.org/alpine/v3.13/releases/x86_64/alpine-virt-3.13.2-x86_64.iso
```

5. 创建一个虚拟硬盘

```bash
qemu-img create -f qcow2 alpine.img 4G
```

随便看着给即可

然后我们编写一个开机脚本方便启动

```bash
vim run.sh
```

输入以下内容

```bash
#!/bin/bash
qemu-system-x86_64 -machine q35 -m 1024 -smp cpus=4 -cpu qemu64 \
-drive if=pflash,format=raw,read-only=on,file=$PREFIX/share/qemu/edk2-x86_64-code.fd \
-netdev user,id=n1,hostfwd=tcp::2222-:22 -device virtio-net,netdev=n1 \
-cdrom alpine-virt-3.13.2-x86_64.iso \
-nographic -hda alpine.img
```

6. 给脚本权限并启动

```bash
chmod +x run.sh
```

```bash
./run.sh
```

启动比较缓慢需要耐心等待，出现让登录时输入 root 即可登录

然后我们输入，对网卡进行配置

```bash
setup-interfaces
```

```bash
 ifup eth0
```

然后一路回车即可

完成后可以尝试 ping 一下网站可以 ping 通就说明一切正常

```bash
ping fengyegf.cn
```

接下来安装 answerfile

```bash
wget https://gist.githubusercontent.com/oofnikj/e79aef095cd08756f7f26ed244355d62/raw/answerfile
```

安装成功后我们输入

```bash
sed -i -E 's/(local kernel_opts)=.*/\1="console=ttyS0"/' /sbin/setup-disk
```

最后我们安装系统到硬盘

```bash
setup-alpine -f answerfile
```

等待安装完成... 可能需要很长时间，具体要看手机的性能，遇到选项回车即可

然后我们看到 alpine:~# 即为成功，随后进行关机

```bash
poweroff
```

输入关机命令后不会立即停止，我们需要等待系统安全的关闭，关机成功后我们修改开机脚本

输入

```bash
vim run.sh
```

修改为以下代码，会出现

```bash
qemu-system-x86_64 -machine q35 -m 2048 -smp cpus=4 -cpu qemu64 \
-drive if=pflash,format=raw,read-only=on,file=$PREFIX/share/qemu/edk2-x86_64-code.fd \
-netdev user,id=n1,hostfwd=tcp::2222-:22,hostfwd=tcp::8081-:80 -device virtio-net,netdev=n1 \
-nographic alpine.img
```

:::caution
BdsDxe: failed to load Boot0001 "UEFI QEMU HARDDISK QM00001 " from PciRoot(0x0)/Pci(0x1F,0x2)/Sata(0x0,0xFFFF,0x0): Not Found

> > Start PXE over IPv4.
> > PXE-E16: No valid offer received.
> > BdsDxe: failed to load Boot0002 "UEFI PXEv4 (MAC:525400123456)" from PciRoot(0x0)/Pci(0x2,0x0)/MAC(525400123456,0x1)/IPv4(0.0.0.0,0x0,DHCP,0.0.0.0,0.0.0.0,0.0.0.0): Not Found

> > Start PXE over IPv6.
> > PXE-E16: No valid offer received.
> > BdsDxe: failed to load Boot0003 "UEFI PXEv6 (MAC:525400123456)" from PciRoot(0x0)/Pci(0x2,0x0)/MAC(525400123456,0x1)/IPv6(0000:0000:0000:0000:0000:0000:0000:0000,0x0,Static,0000:0000:0000:0000:0000:0000:0000:0000,0x40,0000:0000:0000:0000:0000:0000:0000:0000): Not Found

> > Start HTTP Boot over IPv4.....
> > Error: Could not retrieve NBP file size from HTTP server.

Error: Server response timeout.
BdsDxe: failed to load Boot0004 "UEFI HTTPv4 (MAC:525400123456)" from PciRoot(0x0)/Pci(0x2,0x0)/MAC(525400123456,0x1)/IPv4(0.0.0.0,0x0,DHCP,0.0.0.0,0.0.0.0,0.0.0.0)/Uri(): Not Found

> > Start HTTP Boot over IPv6.

:::

修改为一下命令会出现

```bash
qemu-system-x86_64 -machine q35 -m 2048 -smp cpus=4 -cpu qemu64 \
-drive if=pflash,format=raw,read-only=on,file=$PREFIX/share/qemu/edk2-x86_64-code.fd \
-drive file=alpine.img,format=qcow2,if=ide \
-netdev user,id=n1,hostfwd=tcp::2222-:22,hostfwd=tcp::8081-:80 -device virtio-net,netdev=n1 \
-boot order=c \
-nographic
```

用户名称和密码错误，root 提示

:::caution
alpine login: root

Login incorrect

alpine login:
:::
# 结尾
目前没有头绪了，有的可以靠这个命令成功，但是我失败了，如果你有什么方式解决请帮助我改进这个页面，或者在下面留言感谢

持续编写中......
