#cs #front-end #vue 

[ref, reactive 中文文章](https://medium.com/i-am-mike/vue-3-ref-%E8%B7%9F-reactive-%E6%88%91%E8%A9%B2%E6%80%8E%E9%BA%BC%E9%81%B8-2fb6b6735a3c)
[# Ref() vs Reactive() in Vue 3 — what’s the right choice?](https://medium.com/@bsalwiczek/ref-vs-reactive-in-vue-3-whats-the-right-choice-7c6f7265ce39)

---

### introduction
ref, reactive 在被變數受到更改時，會同步template 上有該變數的地方。

EX:
```js
<template>
  {{ person.name }} <!-- will NOT change to Amy -->
  {{ personRef.name }} <!-- will change to Amy -->
  {{ personReactive.name }} <!-- will change to Amy -->
  <button @click="changeName('Amy')" />
</template>

<script>
const App = {
  setup() {
    const person = {name: 'John'};
    const personRef = ref({name: 'John'});
    const personReactive = reactive({name: 'John'});
    const changeName = (name) => {
      person.name = name;
      personRef.value.name = name;
      personReactive.name = name;
    }
    return {
      changeName,
      person,
      personRef,
      personReactive,
    }
  }
}
</script>

```

### differences
1.  ref() → 可以接受任何型態的資料，reactive() → 只接受物件以及陣列
2.  ref() → 需要用.value 去取值，reactive() → 不需用.value 取值
    > refs are unwrapped when they are passed to templates, that’s why you don’t need .value there.
3.  ref() → 不會對物件或陣列內部做監聽(使用 watch 時，reactive() → 會對物件或陣列內部做聽監聽
    > every property in `reactive()` is treated as standalone `ref()`
4.  ref() → 可以直接reasign, reactive → 不行
	ex:
	```js
	// INVALID
	const x = reactive({name: 'John'});
	x = {todo: true};

	// VALID
	const x = ref({name: 'John'});
	x.value = {todo: true};~
	```
	

### when to use?
- 第二篇作者看了看vue ref 的原始碼，說可以把ref 看作以下
	```js
	const myRef = reactive({
	  value: "I'm ref!"
	})

	myRef.value // "I'm ref!"
	myRef.value = "Changed"
	myRef.value // "Changed"
	```
	
- 用reactive 的好時機：
	- 因為reactive 是把裡面的每一個properties 當作ref 對待，所以可以在一個app 需要state container 的時候使用，這樣就可以追蹤所有的state。 EX:
		```js
		const state = reactive({
		  person: {name: 'John'},
		  isLoading: false,
		  updated: true,
		  ...
		})
		```
		

### conclusion 
- 大部分的時間都可以用ref, 可以統一風格並加快開發速度。但同時要記得reactive 的特性，特別可以用在state container 上，在該需求上使用reactive

- 雖然ref 要利用.value 取值，但可以將它視為與一般變數的區別之處

