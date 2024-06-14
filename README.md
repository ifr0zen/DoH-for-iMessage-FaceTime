# DoH-for-iMessage-FaceTime
DNS over HTTPS config profiles for iOS &amp; macOS

本项目参考encrypted-dns https://github.com/paulmillr/encrypted-dns



前言
===
通过iM激活网络抓包发现请求identity.ess.apple.com，而安徽电信湖北电信解析故障如图

<img width="500" alt="合肥电信" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/4a129bf6-75b5-477f-94d4-0d1828712a12"><img width="500" alt="武汉电信" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/18aac24f-d039-4e1d-b6a8-4e680efaf41c">


再附一个安徽联通解析，谁的问题显而易见

<img width="500" alt="芜湖联通" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/55ea2ab5-f283-4b1f-aa53-ac2fd09ec7da">




方法
===
1.下载描述文件安装

https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/releases/download/0.0.1/alibaba-https.mobileconfig
<br> 
<br> 
2.iOS 打开Shadowrocket 配置--本地文件 xxx.conf【默认是default.conf，选择目前使用的conf文件编辑】--i--规则--添加 将激活FT和iM所需的网络请求加入以下规则

**identity.ess.apple.com**    猜测是Apple的ESS服务下的身份验证，这个地址非常重要，关乎到iM登录和同账号下多设备互联互通

**query.ess.apple.com**    猜测是Apple的ESS服务下的查询功能，网络抓包发现在请求这个地址，并且安徽电信解析异常

**push.apple.com**    猜测是推送服务，安徽电信解析异常


<br> 

<img width="200" alt="QQ20240614-231311@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/d7c57174-9e62-4f5e-a9c7-ba04a4c43f9a"><img width="200" alt="QQ20240612-202605@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/b3e69214-fca1-452b-be6c-4ddf5589c57f"><img width="200" alt="QQ20240612-202628@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/ac7e60f6-9dcd-4cae-a694-13b8cddddd52"><img width="200" alt="QQ20240612-202704@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/85725008-5ddf-497b-ac87-43d96fd6547c"><img width="200" alt="QQ20240612-202733@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/9604bac1-79c4-4d57-b3c3-4b4eb9248b31"><img width="200" alt="QQ20240612-202800@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/1d582bf1-765e-467f-9a1f-495e1178cbbb">

<br> 
<br> 
3.重启iOS设备，🚀打开连接，由于第2步添加规则，全局路由选择“配置”
<br> 
<img width="200" alt="QQ20240612-202826@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/f7d076a1-3313-41a9-bf8b-79955f80a9cf">


<br> 
<br> 



4.进入设置激活iM和FT
<br> 
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
2.V2RayU PAC中加入规则

项目地址：[V2rayU](https://github.com/yanue/V2rayU/releases) 



<br> 

<img width="256" alt="QQ20240614-231657@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/e54bdad2-6ab2-4f6f-8fc2-43abc379b709">

<img width="500" alt="QQ20240612-204549@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/26dc1b8d-f6fe-4e6c-9f57-761ce2110ef7">

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
