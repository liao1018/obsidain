#cs #front-end #vue 

# computed
	實際上，若有改動到 computed 當中有與 vue 做綁定的變數(例如 ref, reactive)，computed 就會將該變數設為 dirty，若 template 當中有用到，就會去做一次 computed。這樣可以避免掉過度執行 computed 的情況。
![[Pasted image 20221207231159.png]]
→ 所以，實際上 watch 會都會 computed 先執行。

# watch
## unwatch
	有時
```js
const unwatch = watch(
	() => form.value.a,
	(value) => {
		console.log(value);
	},
);

// 執行以下就可以停止 watch
unwatch();
```

# [[Vue Key]]

# [[Vue v-if v-show 用法]]

# [[Vue v-model]]

# [[Vue v-bind class]]

# [[Vue slot]]