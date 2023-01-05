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

# 實體層
## Ethernet
	為一種最普遍電腦區域網路技術，規定了實體層的連線協定。

## Mac address
	區域網路位址，網路介面卡都有一個獨一無二的識別碼，用來確認網路裝置位置的位址。
	這個識別碼是由六組 16 進位數字組成。

## SSID (Service Set Identifier)
	無線網路名稱，並不是唯一的，可以去更改。公用網路會設定廣播 SSID。
	最大長度不超過32個字符的字母，並且區分大小寫。

## WPA (Wi-Fi Protected Access)
	由 Wi-Fi 聯盟制訂與發佈，用來保護 無線網路 存取安全的技術標準。
	無線網路經過加密，再將網路頻寬分享。


# 網路層
# [[IP(Internal protocol)]]	
## IP (Internet Protocol)
	根據源主機和目的主機的位址來傳送資料。為此目的，IP定義了定址方法和資料包的封裝結構。
	定址和路由 較為複雜
	
## 定址
	定義如何將 IP 位址分配給各個終端節點。

## Router
	所有的網路端點都需要 route，由一些協定決定如何傳送封包。

## Gateway
	閘道，進出的單一入口。可解釋為網路進出要通過的出入口。

## Subnetwork
	允許一個單一的站點能擁有多個區域網路。

## Subnet mask 
	不同類型的 IP 有不同的子網路遮罩，會提供不同的網路及設備數量。
[參考文章](https://nordvpn.com/zh-tw/blog/ziwanglu-zhezhao/)

## DHCP
	設定區域網路中的一台主機為指揮中心 DHCP，可以動態分配 IP，網路中有一台電腦要連結，會動態產生 IP 給該電腦。

# 傳送層
# [[TCP UDP]]

# 應用層
## [[HTTP(Hypertext Transfer Protocol)]]
## [[FTP]]
## SMTP(**S**imple **M**ail **T**ransfer **P**rotocol)
	可用在傳送和接收電子郵件的資訊，但SMTP通常用作傳送電子郵件資訊，而不是接收。
	
## SSH
	一種加密的網路傳輸協定。可在不安全的網路提供安全的傳輸環境，透過安全隧道實現 Client 與 Server 端的溝通。常見技術為遠端登入。

# 其他網路服務
## DNS(Domain Name System) Server
	網際網路的服務，透過 DNS Server，將 Domain Name 與 IP 位址 相互對應。

## VPN(Virtual Private Network)
	將專用網路延伸到公共網路上，使使用者能夠在共享或公共網路上傳送和接收資料，就像他們的計算裝置直接連接到專用網路上一樣，VPN 增加專用網路的功能、安全性和管理，常用於遠端辦公、跨域連線。


