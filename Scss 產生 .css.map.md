 #css 

---

> 讓瀏覽器可以在console中看到位於scss 的第幾行

[參考文章1](https://cssdeck.com/blog/how-to-create-css-map-file/)

- 要先確認電腦有載sass
	```
	sass --version
	```
- 利用—source-map 去產生 .css.map檔
	```
	sass --source-map assets/scss/component_appointmentTVBox_new.scss assets/css/component_appointmentTVBox_new.css
	```
- 還有一些其他的指令，像是watch 等等，可以再去研究

---
