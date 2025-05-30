---
title: 大模型配置
published: 2024-12-18
description: '使用魔塔社区免费的CPU环境配置一个大模型聊天'
image: ''
tags: [大模型,人工智能]
category: '教程分享'
draft: false 
lang: ''
---

# 前言

大模型在目前想必各位都想拥有一个属于自己的吧，一个不受限制，不需要魔法，想聊就聊

# 材料

> [魔塔社区](https://www.modelscope.cn/)账号一个

> 一个聪明的脑子

# 首先

1.进入魔塔社区->个人中心->我的notebook

2.看到魔搭平台免费实例中有一个CPU环境开启运行

![图像](https://github.com/FY-yun/picx-images-hosting/raw/master/20241218/image.4cky15tsw1.webp)

3.开启后点击查看notebook

![图像](https://github.com/FY-yun/picx-images-hosting/raw/master/20241218/image.2veszet0z1.webp)

我们就来到这里了，然后选择Notebook-python3

![图像](https://github.com/FY-yun/picx-images-hosting/raw/master/20241218/image.54xtiwfwpx.webp)

# 配置大模型
因为是CPU运行速度不是很快，考虑到这个问题我们选择来自阿里的通义千问-1.8B（Qwen-1.8B）模型


我们输入
```bash
!git clone https://www.modelscope.cn/qwen/Qwen-1_8B-Chat.git
```
点击播放的按键稍等即可，也可以点击上方加号在创建一个放入命令，效果都一样的

完成后在安装运行代码
```bash
!git clone https://github.com/QwenLM/Qwen.git
```

完成后我们得到两个文件夹我们双击进入Qwen文件夹下点击上方的加号

![图像](https://github.com/FY-yun/picx-images-hosting/raw/master/20241218/image.7p3nvjlr91.webp)

我们需要确定自己是否在文件夹下

![图像](https://github.com/FY-yun/picx-images-hosting/raw/master/20241218/image.5fknc242n9.webp)

如果在就执行

```bash
pip install -r requirements.txt
```

没有就需要cd 目录名称进入对应文件夹下

完成后进入到python的环境中粘贴官方的示例代码

```bash
from transformers import AutoModelForCausalLM, AutoTokenizer, GenerationConfig

model_dir = '模型所在的文件夹'

# Note: The default behavior now has injection attack prevention off.
tokenizer = AutoTokenizer.from_pretrained(model_dir, revision='master', trust_remote_code=True)

# use bf16
# model = AutoModelForCausalLM.from_pretrained("Qwen/Qwen-1_8B-Chat", device_map="auto", trust_remote_code=True, bf16=True).eval()
# use fp16
# model = AutoModelForCausalLM.from_pretrained("Qwen/Qwen-1_8B-Chat", device_map="auto", trust_remote_code=True, fp16=True).eval()
# use cpu only
# model = AutoModelForCausalLM.from_pretrained("Qwen/Qwen-1_8B-Chat", device_map="cpu", trust_remote_code=True).eval()
# use auto mode, automatically select precision based on the device.
model = AutoModelForCausalLM.from_pretrained(model_dir, revision='master', device_map="auto", trust_remote_code=True).eval()

# Specify hyperparameters for generation. But if you use transformers>=4.32.0, there is no need to do this.
# model.generation_config = GenerationConfig.from_pretrained("Qwen/Qwen-1_8B-Chat", trust_remote_code=True) # 可指定不同的生成长度、top_p等相关超参

# 第一轮对话 1st dialogue turn
response, history = model.chat(tokenizer, "你好", history=None)
print(response)
# 你好！很高兴为你提供帮助。

# 第二轮对话 2nd dialogue turn
response, history = model.chat(tokenizer, "给我讲一个年轻人奋斗创业最终取得成功的故事。", history=history)
print(response)
# 这是一个关于一个年轻人奋斗创业最终取得成功的故事。
# 故事的主人公叫李明，他来自一个普通的家庭，父母都是普通的工人。从小，李明就立下了一个目标：要成为一名成功的企业家。
# 为了实现这个目标，李明勤奋学习，考上了大学。在大学期间，他积极参加各种创业比赛，获得了不少奖项。他还利用课余时间去实习，积累了宝贵的经验。
# 毕业后，李明决定开始自己的创业之路。他开始寻找投资机会，但多次都被拒绝了。然而，他并没有放弃。他继续努力，不断改进自己的创业计划，并寻找新的投资机会。
# 最终，李明成功地获得了一笔投资，开始了自己的创业之路。他成立了一家科技公司，专注于开发新型软件。在他的领导下，公司迅速发展起来，成为了一家成功的科技企业。
# 李明的成功并不是偶然的。他勤奋、坚韧、勇于冒险，不断学习和改进自己。他的成功也证明了，只要努力奋斗，任何人都有可能取得成功。

# 第三轮对话 3rd dialogue turn
response, history = model.chat(tokenizer, "给这个故事起一个标题", history=history)
print(response)
# 《奋斗创业：一个年轻人的成功之路》

# Qwen-1.8B-Chat现在可以通过调整系统指令（System Prompt），实现角色扮演，语言风格迁移，任务设定，行为设定等能力。
# Qwen-1.8B-Chat can realize roly playing, language style transfer, task setting, and behavior setting by system prompt.
response, _ = model.chat(tokenizer, "你好呀", history=None, system="请用二次元可爱语气和我说话")
print(response)
# 你好啊！我是一只可爱的二次元猫咪哦，不知道你有什么问题需要我帮忙解答吗？

response, _ = model.chat(tokenizer, "My colleague works diligently", history=None, system="You will write beautiful compliments according to needs")
print(response)
# Your colleague is an outstanding worker! Their dedication and hard work are truly inspiring. They always go above and beyond to ensure that
# their tasks are completed on time and to the highest standard. I am lucky to have them as a colleague, and I know I can count on them to handle any challenge that comes their way.
```
然后点击播放，也就是运行，因为是cpu所以会回复的很慢

效果如图

![图像](https://github.com/FY-yun/picx-images-hosting/raw/master/20241218/image.6wqsdtfa2r.webp)

完美