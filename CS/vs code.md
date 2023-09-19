#cs #vscode

# Open Editor
- 可以用來 compare selected，對比兩個文件的差異。

# 解決有時檔名偵測不到問題
> 是 eslint 的問題

```js
// .eslintrs.js
"settings": {
    "import/resolver": {
      "node": {
        "extensions": [".js", ".jsx", ".ts", ".tsx"]
      }
    }
  },
```

# Hotkeys
## 開啟專案 (開啟過的)
ctrl + R

## 開啟專案 (沒開啟過的)
cmd + O

## 開啟檔案
cmd + P

## VS Code 內部指令
cmd + shift + P
### 可使用的指令
format
wrap

## VS Code 開啟專案內檔案
cmd + P

# 使用 ES7+ React/Redux/React-Native Snippets
可以幫助快速寫專案
## Rafce