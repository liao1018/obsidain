#cs #front-end #vue 

# computed
	實際上，若有改動到 computed 當中有與 vue 做綁定的變數(例如 ref, reactive)，computed 就會將該變數設為 dirty，若 template 當中有用到，就會去做一次 computed。這樣可以避免掉過度執行 computed 的情況。
![[Pasted image 20221207231159.png]]
→ 所以，實際上 watch 會都會 computed 先執行。

# Key
	通常用在 v-for 當中，綁定唯一的 key，讓 Vue 記住你，可以重複利用元素，查看裡面是否需要更改，而不用重新渲染元素，浪費效能。