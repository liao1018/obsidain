#cs #front-end #vue 

[一篇好的英文文章](https://medium.com/vue-mastery/the-best-explanation-of-javascript-reactivity-fea6112dd80d)


# 原始碼說明
![[Pasted image 20221224112057.png]]
![[截圖 2022-12-24 下午11.44.56.png]]

## 概念流程
- 當 Render 出來碰到該 property 的話，因為在 Object.defineProperty 的時候有設置 get 的時候會去儲存該 function 進到該 data 的 subscribes 裏面 (`depend()`)。
- 若之後有去 set 到該 property 的話，除了會去 `dep` 內設置最新值(`internalValue`)以外，還會去透過 `dep.notify()` 去執行每一個 `subscribes` 內的 function。
- 最後去 trigger render。

# 注意事項
-   有些情況 Vue 無法偵測到屬性變化 → 因為 set 偵測不到的時候
    -   Object 一開始宣告所沒有的屬性
    -   …
