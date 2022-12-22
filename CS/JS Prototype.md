#cs #js

# 為什麼需要 prototype
	若是用到 class, 內部有 function 想要提供物件使用，就可以宣告在同一個空間底下，讓函式得以重複利用。
- 利用 prototype 進行串聯
	```js
	function Person(name, age) {
	  this.name = name;
	  this.age = age;
	}
	  
	Person.prototype.log = function () {
	  console.log(this.name + ', age:' + this.age);
	}
	  
	var nick = new Person('nick', 18);
	var peter = new Person('peter', 20);
	  
	console.log(nick.log === peter.log) // true
	  
	// 功能依舊跟之前一樣
	nick.log(); // nick, age:18
	peter.log(); // peter, age:20
	```
	→ this 的值可以參考 [[JS This]]

## new 的行為
1.  利用創建函數A 創造新的object O
2.  O 的proto 指向A 的 prototype
3.  O 當作context(this 的目標)，呼叫A
4.  回傳 O

# 建立 prototype 之後，在 Object 中利用__proto__去取得
```js
function Person(name, age) {
  this.name = name;
  this.age = age;
}
  
Person.prototype.log = function () {
  console.log(this.name + ', age:' + this.age);
}
  
var nick = new Person('nick', 18);
  
// 這個剛講過了，nick.__proto__ 會指向 Person.prototype
console.log(nick.__proto__ === Person.prototype) // true
  
// 那 Person.prototype.__proto__ 會指向誰呢？會指向 Object.prototype
console.log(Person.prototype.__proto__ === Object.prototype) // true
  
// 那 Object.prototype.__proto__ 又會指向誰呢？會指向 null，這就是原型鍊的頂端了
console.log(Object.prototype.__proto__) // null
```
- `Object.prototype` 是原型鏈的底端，沒辦法在取得 __proto__ ㄌㄜˊ。

# 如何看 proto 為誰的 prototype
	看該變數是透過誰宣告出來的。

```js
const obj = {};
obj.__proto__ === Object.prototype; // true
```

