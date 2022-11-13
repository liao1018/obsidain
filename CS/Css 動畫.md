#cs #front-end #css

[Css 動畫比較](https://ithelp.ithome.com.tw/m/articles/10200712)

# Introduction
Css 有以下動畫：
- Transition
- Animation
- Transform

| Type       | Introduction                         | How          | 是否可自行運作             | 效能問題                     |
| ---------- | ------------------------------------ | ------------ | -------------------------- | ---------------------------- |
| Transition | 基礎的 CSS 屬性變化                  | CSS 屬性變化 | 否，須透過偽類或是 JS 事件 | 另一獨立執行緒，較不影響效能 |
| Animation  | 細節的 CSS 屬性變化，可利用 Keyframe | CSS 屬性變化 | 是                         | 另一獨立執行緒，較不影響效能 |
| Transform  | 控制 HTML 元素的縮放、移動等等       | HTML 元素    | 是                         | 會操作 HTML 元素，影響效能   |

# Transition
	有以下種屬性，但可以透過單一屬性 `transition` 去簡寫。
	- transition-property: 要針對哪一個屬性
	- transition-duration: 變化的時長
	- transition-delay: 要隔多久開始執行
	- transition-timimg-function: 要用何種時間曲線去完成動畫

## 單向 Transition
	加在對應的偽類上。

## 雙向 Transition
	可加在原本的選擇器上。