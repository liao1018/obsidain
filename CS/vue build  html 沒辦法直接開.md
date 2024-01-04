#cs #front-end #vue 

---

# publicPath
- publicPath → 如果不是部署在根目錄上的話可使用

## 備註：為什麼 build 完之後的 html 沒辦法直接開啟？
- 因為預設的 public path 是在根目錄上，所以 html 裡面要去找 css, js 檔的時候會 route 到根目錄去找，在本地端根目錄就會是你的電腦，理所當然找不到對應的檔案。
### 如何修改？
> 改用相對路徑去寫。
```js
// vue.config.js
module.exports = {
    publicPath: './'
};
```