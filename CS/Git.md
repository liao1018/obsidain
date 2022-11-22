#cs #git

# discard change 
```shell
git restore .
```

# 把一些檔案從 git 管理中移除
```shell
git rm -rf --cached .
git add .
```

# 設定 user
```shell
git config --global user.name "eric"
git config --global user.email "admin@inncom.cloud"
```

# 更改 commit 訊息
	如果還沒 push 的話...
```shell
git commit --amend
```
→ 會跳出 vim 來編輯，commit message 會在最上面。

[[Git Ignore]]
