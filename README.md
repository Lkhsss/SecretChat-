#  秘密聊天室 - SecretChat
  
  
前段时间突然发现Leancloud的免费功能，于是想写个应用。查看了[官方文档](https://leancloud.cn/docs/ )后发现能干的事挺多。之前写的东西都人模鬼样，于是这次想写一个像样一点的有点实用性的东西。于是写了这个应用。
之所以取名“秘密”其实只是因为数据可以自己在后台查看而已(~~随便想的~~)。其实没啥安全性。
这个程序利用Leancloud提供的免费服务，可以拥有单独的数据库和用户系统(~~白嫖党狂喜~~)。在注册了自己的Leancloud应用后，你们就可以使用leancloud提供的API接口使用这个应用了。
本来官方提供了Python库，但是功能不全(~~不会用~~)，所以自己用rest api写了个类(bushi
  
##  目录
  
  
- [使用教程](#使用教程 )
  - [clone此项目](#clone此项目 )
    - [安装依赖](#安装依赖 )
  - [获取LeanCloud的应用凭证](#获取leancloud的应用凭证 )
    - [创建LeanCloud账户](#创建leancloud账户 )
    - [点击创建应用](#点击创建应用 )
    - [配置应用](#配置应用 )
    - [点击设置](#点击设置 )
    - [选择 设置 > 应用凭证](#选择-设置-应用凭证 )
    - [留存待用](#留存待用 )
  - [配置REST API](#配置rest-api )
  - [运行](#运行 )
    - [创建对话](#创建对话 )
    - [其他操作](#其他操作 )
- [变更记录](#变更记录 )
- [TODO](#todo )
- [开发环境](#开发环境 )
- [开源协议](#开源协议 )
- [另](#另 )
  
##  使用教程
  
  
###  clone此项目
  
点击下载，或者直接在命令行中 `git clone https://github.com/Lkhsss/SecretChat.git`
  
####  安装依赖
  
在项目主目录运行 `pip install -r requirements.txt`安装依赖库
  
这里推荐使用虚拟环境，方便以后打包
  
---
  
###  获取LeanCloud的应用凭证
  
  
####  创建LeanCloud账户
  
  
前往Leancloud控制台([华北节点](https://console.leancloud.cn/ ) 和 [华东节点](https://console-e1.leancloud.cn ) 随便选一个，不要选**国际版**[^为啥不选国际版])，注册一个账号
  
####  点击创建应用
  
  
<img title="" src="https://cdn.staticaly.com/gh/Lkhsss/picx@main/SecretChat/点击创建应用.3tkno01z18o0.webp" alt="点击创建应用" data-align="center" width="388">
  
[^为啥不选国际版]: [国际版自2022年8月起，共享域名不再向中国大陆提供服务](https://forum.leancloud.cn/t/2022-8/25408 )
  
####  配置应用
  
  
这个可以随便填
  
<img title="配置应用" src="https://cdn.staticaly.com/gh/Lkhsss/picx@main/SecretChat/设置应用.5yc1se677hk0.webp" alt="设置应用" width="409" data-align="center">
  
####  点击设置
  
  
<img title="点击设置" src="https://cdn.staticaly.com/gh/Lkhsss/picx@main/SecretChat/点击设置.3gdjxx3omes.webp" alt="点击设置" data-align="center" width="420">
  
####  选择 设置 > 应用凭证
  
  
<img src="https://cdn.staticaly.com/gh/Lkhsss/picx@main/SecretChat/选择应用凭证.6rgsfkootks0.webp" title="选择应用凭证" alt="选择应用凭证" data-align="center" width="300">
  
####  留存待用
  
  
如果此时看到了几个小小黄框框，并且标有`AppID`, `AppKey`, `MasterKey`以及`REST API 服务器地址`，保留网页待用。
  
---
  
###  配置REST API
  
打开主目录下的`leancloud.py`文件
在开头的`REST_API`, `AppID`, `AppKey`, `MasterKey`四项当中分别填入在leancloud控制台中获得的值
<img src="https://cdn.staticaly.com/gh/Lkhsss/picx@main/SecretChat/像这样配置.7303zt6ihsg0.webp" title="像这样配置" alt="像这样配置" data-align="center" width="400">
> 注意看清楚名字，不要填错了
  
> 注意形式和上图保持一致（斜杠和https标头），最好使用网页自带的复制键 -> ![复制键](https://cdn.staticaly.com/gh/Lkhsss/picx@main/SecretChat/复制键.7grz4hsq0ak0.webp )
  
---
  
###  运行
  
运行出来就是酱紫
![运行](https://cdn.staticaly.com/gh/Lkhsss/picx@main/SecretChat/运行.1gxhpgprsbgg.webp )
  
####  创建对话
  
忘了写创建对话的UI了，以后会加上。
现在先手动调用`leancloud.py`创建吧
- 先创建一个新的.py文件
- 写入 
    ```python
    from leancloud import leancloud
  
    Leancloud = leancloud() #初始化
    print(Leancloud.create_conversation("TEST"))
    ```
- - 正常情况下，会返回类似于`{'updatedAt': '', 'name': '', 'objectId': '', 'm': [], 'createdAt': ''}`的信息。
  - 如果出错的话，应该是配置rest api没有配置对，或者代码打错了
  
####  其他操作
  
我在`leancloud.py`中添加了详细的函数方法提示，[CHANGELOG](./CHANGELOG.md ) 中简单地也提到了用法
  
---
  
##  变更记录
  
  
[CHANGELOG.md](./CHANGELOG.md )
  
---
  
##  TODO
  
- [ ] 添加图标支持
- [ ] 写一个**管理端**以用于管理对话和用户
- [ ] 更新英文版README和CHANGELOG(锻炼英语(~~bushi~~)
  
---
  
##  开发环境
  
- 编译器
    - Python 3.9.5 64-bit
- 运行库
    - PyQt5 5.15.4
    - requests 2.28.1
  
---
  
##  开源协议
  
[Apache-2.0 license](https://github.com/Lkhsss/SecretChat/blob/main/LICENSE )
  
---
  
##  另
  
图床挂了记得提个issue踢我一下
  
**欢迎提issues和pr**
  