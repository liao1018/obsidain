#cs #web

[參考文章](https://codecharms.me/posts/security-ssh)

# Introduction
	SSH 是連線加密機制。讓我們在與遠端電腦連線時．能夠將訊息加密後再送出，確保連線不被竊聽。

# Client-Server Model
	要建立一個連線，遠端電腦跑 SSH daemon，預設聽 TCP port 22 進來的連線，認證後提供環境給使用者。SSH client 利用 SSH protocol 來傳送認證訊息與連線細節。

# SSH 與 Public Key Crytography
	public-key 結構中，每一個使用者都有公鑰(public key)與私鑰(secret key)。

- 私鑰：
	- 用來做電子簽名。
	- 用來解密別人利用你公鑰加密的訊息。
- 公鑰：
	- 提供給別人檢查你的電子簽名正確性。
	- 提供給別人加密要給你的訊息。

## 流程舉例
1.  小明用自己的私鑰將訊息簽名。
2.  小明用小美的公鑰將訊息加密。（此時，被加密的訊息連小明也無法還原—只有小美的私鑰可以！）
3.  小明將訊息傳給小美。
4.  小美將訊息用自己的私鑰解密。
5.  小美用小明的公鑰來確認這個訊息是用小明的私鑰簽名的。

## 中間人攻擊(man-in-the-middle-attack)
	在尚未交換公鑰時，如果被調包的話，被認證的人就會變成另一人。
	可利用 PKI (Public Key Infrastructure) 等來解決。

# OpenSSH
	SSH 是一個協定(protocol)，而 OpenSSH 是 SSH 協定的開源實作。
- `sshd` 是 OpenSSH 的 server component，如果是 ssh client，OpenSSH server 就會建立一個遠端操控環境。

# RSA vs DSA
	加密公鑰的演算法們。
- RSA 利用 4096 bits 的長度較預設得 2048 bits 安全。

# Github 舉例
- 產生一組 public & private keys
	```shell-session
	$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
	```
	→ 產生一組 ssh keys，使用 RSA 演算法加密，鑰匙長度 4096 bits，使用 your_email@example.com 作為這組 keys 的標籤。
- 把產生的 public & private keys 加入 ssh-agent (幫忙管理 SSH 的背景程式)
- 將 public key 放到 Github 的 server 上

## 流程
1.  用我們的私鑰去簽名。
2.  用 Github 的公鑰加密指令。
3.  傳送指令到 GitHub server。
4.  GitHub server 用它自己的私鑰解密。
5.  GitHub server 用我們的公鑰來驗證我們的簽名。

# 利用 Terminal 透過 ssh 連線 FTP
```sh
ssh -i {{pem 路徑}} {{user}}@{{host}} -p {{port}}
ssh -i ~/Documents/aws/inncom-key-2022.pem [centos@18.180.18.185](mailto:centos@18.180.18.185) -p 33025
```

- 離開
```sh
exit
```

