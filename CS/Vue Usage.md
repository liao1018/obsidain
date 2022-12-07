#cs #front-end #vue 

# computed
	實際上，若有改動到 computed 當中有與 vue 做綁定的變數(例如 ref, reactive)，computed 就會將該變數設為 dirty，若 template 當中有用到，就會去做一次 computed。這樣可以避免掉過度執行 computed 的情況。
![[Pasted image 20221207231159.png]]
→ 所以，實際上 watch 會都會 computed 先執行。