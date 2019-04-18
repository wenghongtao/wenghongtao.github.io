---
layout: post
title:  "wxpy首次尝试微信机器人自动回复"
categories: python
tags:  python 
author: wenghongtao
---

* content
{:toc}

wxpy首次尝试微信机器人自动回复





## 大概介绍一下

官方网站：https://pypi.org/project/wxpy/0.3.9.8/


从豆瓣上用pip下载

```
pip install -U wxpy -i "https://pypi.doubanio.com/simple/"
```

 - 下面是完整代码，里面有注释
  
  ```
 from wxpy import *
 import re
 
 # 生成机器人实例，启动缓存避免重复登录
 bot = Bot(cache_path=True)
 
 # 在好友列表中搜索名字是“公子羽”性别为男的一项
 found = bot.friends().search('公子羽',sex=1)
 
 # 确保只有一个结果
 boyfriend = ensure_one(found)
 
 bf_rules = {
     r'^.*在[吗|嘛]' : '在呀，找我有啥事呀？？',
     r'^.+[什么|怎么]安排' : '要上班，可能没有空呀！',
     r'^.+[有空]' : '这就不知道了，到时在约你咯！',
     r'^.*[好的|嗯嗯]' : '哈哈就这么说，到时再约！'
 }
 
 @bot.register([boyfriend, bot.self], msg_types = TEXT, except_self = True)
 def reply_bf(msg):
     for rule in bf_rules:
         if re.match(rule, msg.text):
             try:
                 msg.sender.send_msg(bf_rules[rule])
             except ResponseError as e:
                 print(e.err_code,e.err_msg)
             return
 
     return 'OK，测试完成,谢谢！'
 
 # 进入 python 命令行，让程序保持运行
 embed()
  ```
  
  

  - 资源
  
  1. 说明文档 : [http://wxpy.readthedocs.io](http://wxpy.readthedocs.io)
  2. 更新日志 : [https://github.com/youfou/wxpy/releases](https://github.com/youfou/wxpy/releases)
  3. 项目主页 : [https://github.com/youfou/wxpy](https://github.com/youfou/wxpy)
  
 














