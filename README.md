# DoH-for-iMessage-FaceTime
DNS over HTTPS config profiles for iOS &amp; macOS

本项目参考encrypted-dns https://github.com/paulmillr/encrypted-dns

1.下载描述文件安装 https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/releases/download/0.0.1/alibaba-https.mobileconfig

2.iOS 🚀配置--本地文件 xxx.conf【默认是default.conf，选择目前使用的conf文件编辑】--i--规则--添加 apple.com   aaplimg.com   apple-dns.net 将激活FT和iM所需的网络请求加入规则

<img width="577" alt="QQ20240610-142838@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/55cc666a-40f0-49c5-8d4b-9f2875b7963c"><img width="577" alt="QQ20240610-142606@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/a97b3776-2697-4981-9603-1b80da0e03be"><img width="577" alt="QQ20240610-143252@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/cc21d0de-cc44-44aa-b4e4-94be4cbe997f">

3.重启iOS设备，🚀打开连接，由于第2步添加规则，全局路由选择“配置”

<img width="577" alt="QQ20240610-144018@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/9ebf6988-c203-4f2a-81e7-c63eb9d2e6ae">


4.进入设置激活iM和FT

<img width="577" alt="QQ20240610-143909@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/46b2f1dc-b617-485c-bbf1-994fb9f2117b">



如需多设备同步需在其他设备进行相同操作，如Mac
1.安装描述文件
<img width="668" alt="QQ20240610-141324@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/029e82f8-706d-4358-a0bd-239e2f89c319">

2.PAC中加入规则

<img width="700" alt="QQ20240610-141414@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/2fb25587-ef20-413e-b443-6e86c1adb128">

3.重启Mac即可恢复iMessage多设备同步

<img width="429" alt="QQ20240610-142413@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/d42939f2-0670-4660-aae6-be92198fb5f1">
