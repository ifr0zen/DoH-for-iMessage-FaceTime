# DoH-for-iMessage-FaceTime
DNS over HTTPS config profiles for iOS &amp; macOS

本项目参考encrypted-dns https://github.com/paulmillr/encrypted-dns

前言
===
先简单说明一下解决方法的原理再顺便回答几个问题。
首先，iM在激活的时候需要向🍎发送一条国际短信，再通过一些网络请求完成激活，如果有大佬知道更具体的细节可以指导一下，由于出现问题的大部分用户不是新开卡而是最近几天突然不能用的，所以国际短信业务是正常的，而激活iM的网络请求DNS解析是明文，猜测运营商是在这做的文章，相当于你在问路的时候运营商故意给你指了一条错误的路，所以方法中使用了DNS加密，这是iOS14的新功能DoH或者DoT，即DNS over TLS (rfc7858) 和DNS over HTTPS (rfc8484) 以描述文件的形式安装在iOS和macOS，DoH和DoT描述文件结构也比较简单，相关资料是公开的，可自行搜索🔍甚至可以自己编写安装 
除此之外将iM激活过程中的网络请求加入🪜规则中，这样确保iM的激活和使用不受运营商的干扰。
所以大家常问的问题，描述文件激活后可不可以删除？目前来看是不可以的，描述文件和🪜构成当下iM的使用环境，缺一不可。

步骤
===
1.下载描述文件安装

https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/releases/download/0.0.1/alibaba-https.mobileconfig

2.iOS 🚀配置--本地文件 xxx.conf【默认是default.conf，选择目前使用的conf文件编辑】--i--规则--添加 **apple.com   aaplimg.com   apple-dns.net** 将激活FT和iM所需的网络请求加入规则


<img width="300" alt="QQ20240610-142838@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/55cc666a-40f0-49c5-8d4b-9f2875b7963c"><img width="300" alt="QQ20240610-142606@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/a97b3776-2697-4981-9603-1b80da0e03be"><img width="300" alt="QQ20240610-143252@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/cc21d0de-cc44-44aa-b4e4-94be4cbe997f">

3.重启iOS设备，🚀打开连接，由于第2步添加规则，全局路由选择“配置”


<img width="300" alt="QQ20240610-144018@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/9ebf6988-c203-4f2a-81e7-c63eb9d2e6ae">


4.进入设置激活iM和FT


<img width="300" alt="QQ20240610-143909@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/46b2f1dc-b617-485c-bbf1-994fb9f2117b">






如需多设备同步需在其他设备进行相同操作，如Mac
---

1.安装描述文件


<img width="668" alt="QQ20240610-141324@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/029e82f8-706d-4358-a0bd-239e2f89c319">

2.PAC中加入规则

<img width="700" alt="QQ20240610-141414@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/2fb25587-ef20-413e-b443-6e86c1adb128">

3.重启Mac即可恢复iMessage多设备同步

<img width="429" alt="QQ20240610-142413@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/d42939f2-0670-4660-aae6-be92198fb5f1">
