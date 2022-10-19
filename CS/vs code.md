#cs #vscode

# open editor
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