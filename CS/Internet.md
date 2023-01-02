#cs #web

# 學習資源
- [清大開放式課程，計網概](https://hackmd.io/@0xff07/network/https%3A%2F%2Fhackmd.io%2F%400xff07%2FByADDQ57Y)
- [網際網路基礎概論整理](https://hackmd.io/@Yu040419/S1raoZE3E)

# Protocol (協議)
	指格式化的內容，這樣不同語言、不同系統的程式才能透過格式化的標準進行溝通。

像是網頁相關的傳輸要依照HTTP(Hypertext Transfer Protocol)，檔案傳輸則要遵守FTP(File Transfer Protocol)。

# TCP IP 四層協定
將一次傳送不同功能分層，一次做一件事。
![[Pasted image 20221023112911.png]]

| 層級內容 | 層級用意 | 比喻              |
| -------- | -------- | ----------------- |
| 實體層   | 實體傳輸 | 郵差              | 
| IP       | 傳輸地址 | 寄件人,收件人     |
| TCP/UDP  | 傳輸方式 | 三次確認/講求速度 |
| HTTP/FTP | 傳輸格式 | 信件格式          |

# SSID
	無線網路名稱，並不是唯一的，可以去更改。

# WPA(Wi-Fi Protected Access)
	無線網路經過加密，再將網路頻寬分享。

# Mac address
	網路介面卡都有一個獨一無二的識別碼，這個識別碼_是_ 由六組16 進位數字組成。

# Gateway
	閘道，進出的單一入口。Router 有時候就可以是一個 Gateway。

# Subnet mask 
	不同類型的 IP 有不同的子網路遮罩，會提供不同的網路及設備數量。
[參考文章](https://nordvpn.com/zh-tw/blog/ziwanglu-zhezhao/)

# DHCP
	設定網路中的一台主機為指揮中心 DHCP，可以動態分配 IP，網路中有一台電腦要連結，會動態產生 IP 給該電腦。

# DNS(Domain Name System) Server
	透過 DNS Server，將 Domain Name 轉為 IP 位址。

# [[IP(Internal protocol)]]	

# VPN
	透過遠端主機更換地址，多人共用地址等。
	安全加密，切換 IP。

# [[TCP UDP]]

# [[FTP]]

# [[HTTP(Hypertext Transfer Protocol)]]
