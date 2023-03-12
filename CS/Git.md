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

# 還原已經 Push 的提交
## revert
	可以新增一個 Commit 來反轉另一個 Commit 的內容，原本的 Commit 依舊還是會保留在歷史紀錄中。在團隊中使用較為適合，對其他人來說就不算更改歷史，而是新增一筆提交。
```sh
git revert HEAD
git revert <sha>
```
## reset 
	可以直接拆除 commit，更改歷史，通常用於一人的專案中，在團隊中則會有影響團隊歷史的風險。
```sh
# 往前一個 commit
git reset HEAD^
```

[[Git Ignore]]
