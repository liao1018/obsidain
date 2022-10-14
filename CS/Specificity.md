#cs #front-end #css

---

# 原則
1.  兩個選擇器作用在同一元素，以權重高的為優先
2.  如果相同權重，以後面寫的為優先

# 基本權重優先度
inline style > ID > Class > Element > *

# 判斷方式
> 利用四位數X-Y-Z-W 來判斷

1.  ＊ → 為0-0-0-0
    
2.  Element
    
    EX: li, ul, div, …
    
    → 為0-0-0-1
    
3.  class
    
    → 0-0-1-0
    
    -   除此之外，以下也是跟class 一樣為 0-0-1-0
        -   psuedo-class
            
            冒號開頭，ex: :hover, :focus
            
        -   attribute
            
            [type:checkbox]、[attr]
            
4.  id
    
    → 0-1-0-0
    
5.  inline style
    
    → 1-0-0-0

# 舉例
```js
ul>li 都是 element 所以加起來是 0-0-0-2

body div ul li a span 總共 6 個 element 所以加起來是 0-0-0-6

li.myclass 一個 element 加上一個 class ，所以是 0-0-1-1

li.myclass ~ li 兩個 element 加上一個 class ，所以是 0-0-1-2

form input[type=email] 兩個 element 、一個 attribute，所以是 0-0-1-2
```

# 注意事項
!important 是大魔王，只有大魔王能超過大魔王，沒事不要亂用

---

