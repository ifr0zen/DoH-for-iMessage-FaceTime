# DoH-for-iMessage-FaceTime
DNS over HTTPS config profiles for iOS &amp; macOS

本项目参考encrypted-dns https://github.com/paulmillr/encrypted-dns



前言
===
通过iM激活网络抓包发现请求identity.ess.apple.com，而安徽电信湖北电信解析故障如图

<img width="500" alt="合肥电信" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/4a129bf6-75b5-477f-94d4-0d1828712a12"><img width="500" alt="武汉电信" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/18aac24f-d039-4e1d-b6a8-4e680efaf41c">


再附一个安徽联通解析，谁的问题显而易见

<img width="500" alt="芜湖联通" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/55ea2ab5-f283-4b1f-aa53-ac2fd09ec7da">


资料
===
pod2g(上古iOS越狱大佬)和gg关于iMessage中间人攻击报告中有介绍iMessage工作流程，感兴趣可下载[iMessage_privacy.pdf](https://github.com/user-attachments/files/15895563/iMessage_privacy.pdf)


<img width="500" alt="QQ20240619-120924@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/2f454f92-d323-4a4f-8e87-35028a630d97"> <img width="500" alt="QQ20240619-124735@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/9971ec74-7a47-4785-8f2d-556e6b77702e">






方法
===
1.下载描述文件安装

https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/releases/download/0.0.1/alibaba-https.mobileconfig
<br> 
<br> 
2.iOS 打开Shadowrocket 配置--本地文件 xxx.conf【默认是default.conf，选择目前使用的conf文件编辑】--i--规则--添加 参考图示将激活FT和iM所需的网络请求加入规则中


**identity.ess.apple.com**    猜测是Apple的ESS服务下的身份验证，这个地址非常重要，关乎到iM登录和同账号下多设备互联互通

**query.ess.apple.com**    猜测是Apple的ESS服务下的查询功能，网络抓包发现在请求这个地址，并且安徽电信解析异常

**rand(0,255)-courier.push.apple.com**    资料解释为iMessage使用的PUSH协议，用于客户端证书验证 注：rand(0,255)为0~255随机数，具体如0-courier.push.apple.com  11-courier.push.apple.com 222-courier.push.apple.com等



<br> 


<img width="200" alt="QQ20240619-130317@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/ad60645b-39a5-4e5b-b4be-9b450c179bbe"><img width="200" alt="QQ20240612-202605@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/b3e69214-fca1-452b-be6c-4ddf5589c57f"><img width="200" alt="QQ20240612-202628@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/ac7e60f6-9dcd-4cae-a694-13b8cddddd52"><img width="200" alt="QQ20240612-202704@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/85725008-5ddf-497b-ac87-43d96fd6547c"><img width="200" alt="QQ20240619-130358@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/8cfa7acb-86a7-4151-8d2e-1e463199a321"><img width="200" alt="QQ20240619-130425@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/f41bfc75-8e0e-417a-80b9-68b3f8c18596"><img width="200" alt="QQ20240619-130451@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/7596e7be-5ebc-4ed4-af99-9efe4201c3ec"><img width="200" alt="QQ20240619-130302@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/02b4f6de-72db-440e-b153-32110882495d">





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





如需多设备同步需在其他设备进行相同操作，如Mac
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
<img width="500" alt="QQ20240610-142413@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/d42939f2-0670-4660-aae6-be92198fb5f1">

进阶
===
经过以上操作电信用户应该成功激活iM和FT，Apple设备也恢复互联互通，若想移除描述文件可参考以下方法。

先挖个坑吧，后面看能不能填上。

思路是通过App特性实现DoH，但是实测效果不是特别好，收益不大。
