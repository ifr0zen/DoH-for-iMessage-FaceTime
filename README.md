# DoH-for-iMessage-FaceTime
DNS over HTTPS config profiles for iOS &amp; macOS

本项目参考encrypted-dns https://github.com/paulmillr/encrypted-dns

更新
===
6月24日安徽电信已恢复正常路由，6月27日湖北电信也恢复正常路由

安徽电信、湖北电信用户可移除描述文件(若安装)，VPN中删除相应规则




前言
===
通过iM激活网络抓包发现请求identity.ess.apple.com，而安徽电信湖北电信路由追踪如图

<img width="500" alt="合肥电信" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/4a129bf6-75b5-477f-94d4-0d1828712a12"><img width="500" alt="武汉电信" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/18aac24f-d039-4e1d-b6a8-4e680efaf41c">


再附一个安徽联通路由追踪，谁的问题显而易见

<img width="500" alt="芜湖联通" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/55ea2ab5-f283-4b1f-aa53-ac2fd09ec7da">


资料
===
pod2g(上古iOS越狱大佬)和gg关于iMessage中间人攻击报告中有介绍iMessage工作环境，感兴趣可下载[iMessage_privacy.pdf](https://github.com/user-attachments/files/15895563/iMessage_privacy.pdf)


<img width="500" alt="QQ20240619-120924@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/2f454f92-d323-4a4f-8e87-35028a630d97"> <img width="500" alt="QQ20240619-124735@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/9971ec74-7a47-4785-8f2d-556e6b77702e">








iPhone&iPad
---

1.下载描述文件安装



https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/releases/download/0.0.1/alibaba-https.mobileconfig

<br> 
<br> 
2.iOS 打开Shadowrocket 配置--本地文件 xxx.conf【编辑当前使用的conf文件，至少是default.conf】--i--规则--添加 参考图示将激活FT和iM所需的网络请求加入规则中


<br> 


<img width="200" alt="QQ20240619-130317@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/ad60645b-39a5-4e5b-b4be-9b450c179bbe"><img width="200" alt="QQ20240612-202605@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/b3e69214-fca1-452b-be6c-4ddf5589c57f"><img width="200" alt="QQ20240612-202628@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/ac7e60f6-9dcd-4cae-a694-13b8cddddd52"><img width="200" alt="QQ20240612-202704@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/85725008-5ddf-497b-ac87-43d96fd6547c"><img width="200" alt="QQ20240619-130358@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/8cfa7acb-86a7-4151-8d2e-1e463199a321"><img width="200" alt="QQ20240619-130425@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/f41bfc75-8e0e-417a-80b9-68b3f8c18596"><img width="200" alt="QQ20240619-130451@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/7596e7be-5ebc-4ed4-af99-9efe4201c3ec"><img width="200" alt="QQ20240619-130302@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/02b4f6de-72db-440e-b153-32110882495d">







**identity.ess.apple.com**    猜测是Apple的ESS服务下的身份验证，安徽电信路由追踪异常，这个地址非常重要，似乎关系到iM登录和同账号下多设备连续互通

**query.ess.apple.com**    猜测是Apple的ESS服务下的查询服务，网络抓包发现在请求这个地址，并且安徽电信路由追踪异常

**rand(0,255)-courier.push.apple.com**    资料解释为iMessage使用的PUSH服务，属于APNs 注：rand(0,255)为0~255随机数，具体如0-courier.push.apple.com  11-courier.push.apple.com等，需要注意这里的写法与前面两条不同，使用Domain-KEYWORD,即匹配域名关键词，具体请看截图内容，如果图省事与前面两条写法相同使用Domain-SUFFIX直接填push.apple.com也可以，效果相同，但会将Apple其他push服务也列入规则代理，如api.push.apple.com，gateway.push.apple.com等，所以截图写法更为精确，但列入也不一定是坏事，这个看个人选择。

**如果对这些不太了解请严格按照上方截图填写并核对。**


<br> 


<br> 





以下是通过相关资料大致得出iMessage工作流程，个人理解仅供参考，如有错误烦请指正。
--

首先iM基于Apple的一项服务，称之为ESS Servers，该服务用于存储iMessage用户的所有公共加密密钥，并且从IP地址上看似乎位于库比提诺的Apple Park。iM登录的时候会先完成身份验证identity.ess.apple.com

但用户A发送iMessage短信时并不会简单的从用户A的iPhone发送到用户B的iPhone，用户A会先向ESS Servers查询用户B的身份，此时用户A的iPhone会请求query.ess.apple.com，成功后ESS Servers向用户A返回用户B的加密密钥。有了这些信息，用户A的iPhone加密消息，将加密文本发送给Apple，然后Apple将其转发给用户B，随后用户B的iPhone可以对其进行解密显示内容，所以iMessage被称为“端到端加密”。即每次合法用户想要向新收件人发送iMessage时，都会访问Apple密钥分发系统。iMessages客户端首先联系 query.ess.apple.com 以查找给定用户名的密钥。作为响应，服务器返回用户的公钥、状态和推送令牌，用于向用户发送APNs通信。






<br> 
<br> 
3.重启iOS设备，🚀打开连接，由于第2步添加规则，全局路由选择“配置”



<br>



<img width="200" alt="QQ20240612-202826@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/f7d076a1-3313-41a9-bf8b-79955f80a9cf">




<br> 
<br> 



4.进入设置激活iM和FT

<img width="200" alt="QQ20240612-203723@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/bc641f92-0efe-4d47-a673-44ce240571d2">


<br> 
<br> 

<br> 





Mac
---
<br> 

1.安装描述文件 




<img width="500" alt="QQ20240610-141324@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/029e82f8-706d-4358-a0bd-239e2f89c319">
<br> 
<br> 
2.V2RayU PAC中加入上方列出的三条规则

项目地址：[V2rayU](https://github.com/yanue/V2rayU/releases) 



<br> 

<img width="256" alt="QQ20240614-231657@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/e54bdad2-6ab2-4f6f-8fc2-43abc379b709">

<img width="500" alt="QQ20240619-134939@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/098804da-193c-43c4-bb91-8df55fb4515b">



<br> 
<br> 
3.重启Mac即可恢复iMessage多设备同步


<br> 
<img width="450" alt="QQ20240623-202156@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/1d26222e-343b-422b-b45b-280a4d14e56f">
<img width="400" alt="QQ20240623-203239@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/59d788a9-386b-4b66-8aa0-366a4cb4d3b4">
<br> 
<br> 


4.注意⚠️ 如iPhone向Mac转发短信出现延迟现象请做如下操作或在iPhone上安装描述文件

<img width="200" alt="QQ20240623-203942@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/b73f76d3-97b6-4b80-b461-dbb066a8f7ef"><img width="200" alt="QQ20240623-204002@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/8f311738-9559-4d73-9a6e-6db71c9cdeff"><img width="200" alt="QQ20240623-204031@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/d38a6146-8385-43e3-ab7a-d8c9d61f4d9b">










