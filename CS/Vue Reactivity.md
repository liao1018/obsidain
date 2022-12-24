#cs #front-end #vue 

[一篇好的英文文章](https://medium.com/vue-mastery/the-best-explanation-of-javascript-reactivity-fea6112dd80d)

-   Vue 當中，data 當中每一個 property 都會去利用 Object.defineProperty 去設定 get, set 的時候要做啥
    -   get: 儲存 get 的那個 function 到陣列 subscribers，讓以後若有 set 的時候可以直接重複使用
    -   set: 當該 property 被設定的時候會觸發該 property 的 notify()，要去將該 property 的 subscribers 全部執行一次。
-   有些情況 Vue 無法偵測到屬性變化 → 因為 set 偵測不到的時候
    -   Object 一開始宣告所沒有的屬性
    -   …

![[Pasted image 20221224112057.png]]