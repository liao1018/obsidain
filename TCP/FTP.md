#cs #web 

# 可透過 FileZilla 做連接
## 新增站台
	Advanced 裡面可以去選預設的 remote directory。

# SFTP
	todo
	可以利用 key pem，裡面包涵 public key, private key。
## 利用 Terminal 透過 ssh 連線 FTP
```sh
ssh -i {{pem 路徑}} {{user}}@{{host}} -p {{port}}
ssh -i ~/Documents/aws/inncom-key-2022.pem [centos@18.180.18.185](mailto:centos@18.180.18.185) -p 33025
```

- 離開
```sh
exit
```