#js

---

# 在瀏覽器運行
要在瀏覽器運行import/export 要加上這段
```js
<script type="module"></script>
```


> 分成不具名匯出/匯入和具名匯出/匯入。

### 不具名
-  不具名匯出(export default)
	有以下兩點特性：
	1. 不具名，在import 的時候可以自己取名字
	2. 一個file只能有一個export default
	```js
	// 直接匯出	
	export default 1;
	// 匯出變數
	const a = 1
	export default a;
	// 匯出匿名函式
	export default function() {
	  console.log('這是一段函式');
	}
	// 多個變數可以包在object
	const obj = { name: 'obj' };
	const obj2 = { name: 'obj2' };
	export default { obj, obj2 };
	```

- 不具名匯入
	直接匯入，要賦予名稱
	```js
	// export file
	export default function() {
	  console.log('這是一段函式');
	}
	
	// import file
	import fn from './defaultModule.js';
	fn(); // 直接執行函式
	```

### 具名
- 具名匯出(export)
	- import 時要相同名稱才可以匯入，除非使用更改名字
	- 一個file 可以有多個export
	```js
	// let, const 純值
	export let a = 1;
	export let obj = { name: 'obj'};
	// 具名方法
	export function fn() {
	  console.log('這是一段函式')
	}
	// 多個變數可以包在object
	const b = 2;
	const obj2 = { name: 'obj2' };
	const obj3 = { name: 'obj3' };
	
	export { b, obj2, obj3 };
	// 以上等同於以下
	export const b = 2;
	export const obj2 = { name: 'obj2' };
	export const obj3 = { name: 'obj3' };
	```
- 具名匯入(import)
	- 要使用解構的方式匯入
		```js
		// export file
		export const obj = { name: 'obj'}; // 此段如果沒有被匯入，則無法運作
		export function fn() {
		  console.log('這是一段函式')
		}
		
		// import file
		import { fn } from './module.js';
		fn();
		```
	- 可以重新命名
		```js
		// export file
		export const obj = { name: 'obj'};
		export function fn() {
		  console.log('這是一段函式')
		}
		
		// import file
		import { fn as newFn, obj as newObj } from './module.js';
		newFn();
		```
	- 可以全部匯入
		```js
		// import file 全部匯入並賦予至一個物件上
		import * as name from './module.js';
		name.fn();
		console.log(name.obj);
		```
### 同時匯入
- 可以同時具名&不具名匯出，接著一起匯入 -> 但其實沒有必要
	```js
	// export file
	export const obj = { name: 'obj' };
	export default function() {
	  console.log('這是一段函式');
	}
	
	// import file
	import fn, * as named from './defaultModule.js';
	fn();
	console.log(named.obj);
	// 其中 name.default === fn;
	console.log(named.default === fn); // true
	```
---

