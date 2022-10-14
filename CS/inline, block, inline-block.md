#cs #front-end #css

[參考文章](https://ytclion.medium.com/css%E6%95%99%E5%AD%B8-%E9%97%9C%E6%96%BCdisplay-inline-inline-block-block%E7%9A%84%E5%B7%AE%E5%88%A5-1034f38eda82)

---

> html中，每一個標籤都會有預設的display屬性，分為inline 或是block。而display 屬性大致分為inline、block、inline block。
- inline element
	span, a, input,...
- block element
	div, p, ul, li, h1,...
- inline-block
	img

### 注意
- inline 元素裡面不應該放block 元素

---

### inline, block, inline-block 區別
[自己寫的codepen，測試inline, inline-block](https://codepen.io/0612203/pen/QWmKomx?editors=1100)


### inline
- 在同一行呈現
- 不可設定長寬，由內部撐開
- 可以設定padding、margin，但不會影響到其他元素。如圖
	![[Pasted image 20220713234500.png]]
	- 也不會影響到container，container 不會因為inline element有設定padding, margin 而被撐開
### block
- 會自動換行
- 寬度自動佔滿
- 可設定長寬
- 可設定margin、padding
### inline-block
> 對外是inline、對內是block
- 在同一行呈現
- 可設定長寬
- 可設定margin, padding，且可以影響到其他元素