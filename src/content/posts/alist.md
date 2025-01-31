---
title: alist
published: 2025-01-06
description: '本期主要教学alist的配置和食用方法'
image: 'https://github.com/FY-yun/picx-images-hosting/raw/master/20250115/thumbnail.361nx10tkw.webp'
tags: [alist,termux]
category: '教程分享'
draft: false 
lang: ''
---

# 配置

首先你得先安装alist，至于安装教程肯定是[点击跳转](https://fengyegf.cn/blog/posts/android/1/)

要是看不懂这边给你来一个大白话版本的,没脑子就按着点击复制粘贴
> 1.首先确保你的termux源
输入
```bash
pkg update
```
> 2.安装alist
```bash
pkg install alist
```
> 3.启动alist
```bash
alist server
```
初次启动密码会显示在命令行，复制密码

<img src="https://1drv.ms/i/c/2182f48b953d36f8/IQSQhWfpo8LaQLcZt3aYXiBOAZm_EEndjYKrHea5v9wcpCU?width=1024" width="1024" height="auto" />

打开浏览器访问
```bash
http://127.0.0.1:5244/
```
> 登录
用户名
```bash
admin
```
密码为你在命令行复制的

# 食用

<img src="https://1drv.ms/i/c/2182f48b953d36f8/IQSt4kP3riT2R7s-qu3EW57RAYKVSq5JXnHQJb7nAD04SYo?width=1024" width="1024" height="auto" />

默认登录后会到达，如果没有就点击下面的管理

<img src="https://1drv.ms/i/c/2182f48b953d36f8/IQRdeUtFOfUlSK1eistlT-wKAVb_KIctyzQn3KGwQuBRByo?width=1024" width="1024" height="auto" />

# 储存添加

点击储存->点击添加->选择驱动->本地储存

<img src="https://1drv.ms/i/c/2182f48b953d36f8/IQSrfBJzgdtpRYRQ_-D7O7V_ATsKfYjGPN44418BPGlejX8?width=1024" width="1024" height="auto" />

需要注意安卓的目录，这里选择对应的

# 配置离线下载

<img src="https://1drv.ms/i/c/2182f48b953d36f8/IQQVnB16rli8Tos0XvqQxQuOAR68aCw75G3B6zVsyWDqwWI?width=1024" width="1024" height="auto" />

由于在之前文章有讲这里就跳过

# 美化

<img src="https://1drv.ms/i/c/2182f48b953d36f8/IQTcqqhIZVs3Q7wx67YnjWcwAaj1C1p1zIb_0DxqoDpSvNs?width=1024" width="1024" height="auto" />

代码给出了图像加部分美化

```JavaScript
<style>
/*白天背景图*/
 .hope-ui-light {
    background-image: url("https://github.com/FY-yun/picx-images-hosting/raw/master/20241217/2293F77B1F19B0A4ED6606A0027F8E46.1ap1yxyt8s.webp") !important;
    background-repeat:no-repeat;
    background-size:cover;
    background-attachment:fixed;
    background-position-x:center;
}
/*夜间背景图*/
 .hope-ui-dark {
    background-image: url("https://image.baidu.com/search/down?url=https://tva1.sinaimg.cn/large/007Dxz4Tgy1hrgu4y6wo8j31hc0u04qp.jpg") !important;
    background-repeat:no-repeat;
    background-size:cover;
    background-attachment:fixed;
    background-position-x:center;
}
/*主列表白天模式透明*/
 .obj-box.hope-stack.hope-c-dhzjXW.hope-c-PJLV.hope-c-PJLV-igScBhH-css {
    background-color: rgba(255, 255, 255, 0) !important;
}
/*主列表夜间模式透明*/
 .obj-box.hope-stack.hope-c-dhzjXW.hope-c-PJLV.hope-c-PJLV-iigjoxS-css {
    background-color:rgb(0 0 0 / 0%) !important;
}
/*readme白天模式透明*/
 .hope-c-PJLV.hope-c-PJLV-ikSuVsl-css {
    background-color: rgba(255, 255, 255, 0.2) !important;
}
/*readme夜间模式透明*/
 .hope-c-PJLV.hope-c-PJLV-iiuDLME-css {
    background-color:rgb(0 0 0 / 20%) !important;
}

/*顶部右上角切换按钮透明*/
 .hope-ui-light .hope-c-ivMHWx-hZistB-cv.hope-icon-button {
    background-color: rgba(255, 255, 255, 0) !important;
}
.hope-ui-dark .hope-c-ivMHWx-hZistB-cv.hope-icon-button {
    background-color:rgb(0 0 0 / 0%) !important;
}
/*右下角侧边栏按钮透明 第一个是白天 第二个是夜间*/
 .hope-ui-light .hope-c-PJLV-ijgzmFG-css {
    background-color: rgba(255, 255, 255, 0) !important;
}
.hope-ui-dark .hope-c-PJLV-ijgzmFG-css {
    background-color:rgb(0 0 0 / 0%) !important;
}

/*白天模式代码块透明*/
 .hope-ui-light pre {
    background-color: rgba(255, 255, 255, 0.1)!important;
}
/*夜间模式代码块透明*/
 .hope-ui-dark pre {
    background-color: rgba(255, 255, 255, 0.1)!important;
}

/*左侧侧边栏目录*/
/*白天模式*/
 .hope-ui-light .hope-c-PJLV-ieGWMbI-css {
    background: rgba(255, 255, 255, 0) !important;
}
/*夜间模式*/
 .hope-ui-dark .hope-c-PJLV-ieGWMbI-css {
    background-color:rgb(0 0 0 / 0%) !important;
}

/* 返回顶部 */
 .hope-c-PJLV-ihVEsOa-css {
    background: rgba(255, 255, 255, 0.5) !important;
}
.hope-ui-dark .hope-c-PJLV-ihVEsOa-css {
    background-color:rgb(0 0 0 / 50%) !important;
}

/*正常情况未使用吸附功能*/
/*顶部*/
 .hope-c-PJLV-ikaMhsQ-css {
    background: rgba(255, 255, 255, 0) !important;
}
/*导航条*/ 
/*白天模式*/
 .hope-ui-light .hope-c-PJLV-idaeksS-css {
    background-color: rgba(255, 255, 255, 0) !important;
    border-radius: var(--hope-radii-xl) !important;
}
/*夜间模式*/
 .hope-ui-dark .hope-c-PJLV-idaeksS-css {
    background-color:rgb(0 0 0 / 0%) !important;
    border-radius: var(--hope-radii-xl) !important;
}
/* 吸附到页面顶部 */
/*顶部*/
 .hope-c-PJLV-icWrYmg-css {
    background: rgba(255, 255, 255, 0) !important;
}
/*导航条*/
 .hope-c-PJLV-icKsjdm-css::after {
    background: rgba(255, 255, 255, 0) !important;
}
/*白天模式*/
 .hope-ui-light .hope-c-PJLV-icKsjdm-css {
    background-color: rgba(255, 255, 255, 0) !important;
    border-radius: var(--hope-radii-xl) !important;
}
/*夜间模式*/
 .hope-ui-dark .hope-c-PJLV-icKsjdm-css {
    background-color:rgb(0 0 0 / 0%) !important;
    border-radius: var(--hope-radii-xl) !important;
}
/*仅吸附导航栏*/
/*导航条*/
 .hope-c-PJLV-ifdXShc-css::after {
    background: rgba(255, 255, 255, 0) !important;
}
/*白天模式*/
 .hope-ui-light .hope-c-hrsMRY {
    background-color: rgba(255, 255, 255, 0.5) !important;
    border-radius: var(--hope-radii-xl) !important;
}
/*夜间模式*/
 .hope-ui-dark .hope-c-hrsMRY {
    background-color:rgb(0 0 0 / 50%) !important;
    border-radius: var(--hope-radii-xl) !important;
}
/*路径栏透明*/
.hope-ui-dark .hope-c-PJLV-idaeksS-css {
    background-color:rgb(0 0 0 / 0%) !important;
}
.hope-ui-light .hope-c-PJLV-idaeksS-css {
    background-color:rgb(0 0 0 / 0%) !important;
}
/*markdown大纲透明*/
.hope-c-PJLV-igmvEDM-css {
    background-color:rgb(0 0 0 / 0%) !important;
}
</style>
```

# 结束
