#cs #cs-basic-ability 


# Introduction
	Warp is a blazingly fast, Rust-based terminal that makes you and your team more productive at running, debugging, and deploying code.
[官方文件](https://docs.warp.dev/getting-started/readme)

## 一些簡易好用的地方
- Lile a code editor，比較好編輯、複製、選取。
- Easy to copy commands, outputs.(可以直接複製 block 中的 commands, outputs or both.)
未來：
- Run your documentation inside the terminal

## Hotkeys
| hotkey              | action              |
| ------------------- | ------------------- |
| cmd + p             | 打開搜尋列          |
|  control + `         | A.I. Command Search |
| control + shift + r | 開啟 workflow       |
 
# Warp 支援的 shells 
	like Bash, Zsh, and Fish...
## Zsh
	Zsh is the default shell on macOS(starting with macOS Catalina in 2019), replacing Bash shell which.

`$ zsh --version` → check version of Zsh.

### Customize Your Zsh Shell Environment
	modify the .zshrc file which is located your home directory (~/.zshrc).
	可視 .zshrc 為啟動 zsh instance 時會執行的檔案。可以客製化一些行為：設定環境變數、新增別名(alias)、changing the prompt(?)...

### Editing the .zshrc file
`nano ~/.zshrc` or `vi ~/.zshrc`.

### 設定完之後記得要重新啟動 Zsh instace
	可以 restart warp, terminal or type `source ~/.zshrc`.

# 功能們
##  A.I. Command Search
	可以利用 natural language 去搜尋 executable commands。
	
## 開啟 workflow
	可以去搜尋 commands.dev in warp，快速透過指令執行 workflows。
	→ 快捷鍵：control + shift + r
[commands.dev](https://www.commands.dev/)
 
- 可以創建自己的 workflows。