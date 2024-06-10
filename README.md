# DoH-for-iMessage-FaceTime
DNS over HTTPS config profiles for iOS &amp; macOS

本项目参考encrypted-dns https://github.com/paulmillr/encrypted-dns

1.下载描述文件安装 [Uploading alibaba-https.mobileconfig…](<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>PayloadContent</key>
	<array>
		<dict>
			<key>DNSSettings</key>
			<dict>
				<key>DNSProtocol</key>
				<string>HTTPS</string>
				<key>ServerAddresses</key>
				<array>
					<string>2400:3200::1</string>
					<string>2400:3200:baba::1</string>
					<string>223.5.5.5</string>
					<string>223.6.6.6</string>
				</array>
				<key>ServerURL</key>
				<string>https://dns.alidns.com/dns-query</string>
			</dict>
			<key>PayloadDescription</key>
			<string>Configures device to use AliDNS Encrypted DNS over TLS</string>
			<key>PayloadDisplayName</key>
			<string>AliDNS DNS over HTTPS</string>
			<key>PayloadIdentifier</key>
			<string>com.apple.dnsSettings.managed.9d6e5fdf-e404-4f34-ae94-27ed2f636ac4</string>
			<key>PayloadType</key>
			<string>com.apple.dnsSettings.managed</string>
			<key>PayloadUUID</key>
			<string>35d5c8a0-afa6-4b36-a9fe-099a997b44ad</string>
			<key>PayloadVersion</key>
			<integer>1</integer>
			<key>ProhibitDisablement</key>
			<false/>
		</dict>
	</array>
	<key>PayloadDescription</key>
	<string>Adds the AliDNS to Big Sur and iOS 14 based systems</string>
	<key>PayloadDisplayName</key>
	<string>AliDNS over HTTPS</string>
	<key>PayloadIdentifier</key>
	<string>com.paulmillr.apple-dns</string>
	<key>PayloadRemovalDisallowed</key>
	<false/>
	<key>PayloadType</key>
	<string>Configuration</string>
	<key>PayloadUUID</key>
	<string>A4475135-633A-4F15-A79B-BE15093DC97A</string>
	<key>PayloadScope</key>
	<string>System</string>
	<key>PayloadVersion</key>
	<integer>1</integer>
</dict>
</plist>
)

2.iOS 🚀配置--本地文件.conf--i--规则--添加 apple.com   aaplimg.com   apple-dns.net
![IMG_3742](https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/cfbecd9e-6dad-4689-b175-583511b2c216)![IMG_3743](https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/976446a2-0347-4a9f-8f3d-04936bca4909)
3.重启iOS设备，🚀选择配置后打开连接
![IMG_3744](https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/89f946b5-d961-46b3-aeaf-8087efb0a242)
4.激活iM和FT

如需多设备同步需在其他设备进行相同操作，如Mac
1.安装描述文件
<img width="668" alt="QQ20240610-141324@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/029e82f8-706d-4358-a0bd-239e2f89c319">
2.PAC中加入规则
<img width="700" alt="QQ20240610-141414@2x" src="https://github.com/ifr0zen/DoH-for-iMessage-FaceTime/assets/17274321/2fb25587-ef20-413e-b443-6e86c1adb128">


