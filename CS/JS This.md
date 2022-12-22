#cs #js

# Introduction
	this有意義的地方只有在物件的時候，且this難懂的原因是他在任何地方都有有相對應的值。

- 最宏觀角度去看 this：
	1. 嚴格模式下是 `undefined`
	2. 非嚴格模式下，瀏覽器是 `window`
	3. 非嚴格模式下，node.js 是 `global`

在了解 this 之前，先去了解以下三個 function:

# `call, apply, bind`
	以上三者都有能力去改變 function 中 this 的值，
	call, apply 會直接 call function, 
	bind 則會回傳綁定過後的 function。

- `call, apply` 是類似的 function，只是參數傳入的方式不同。
	- `call`: `(要綁定this的值, ...arguments)`
	- `apply`: `(要綁定this的值, [...arguments])`
	```js
	'use strict';
	function hello(a, b){
	  console.log(this, a, b)
	}
	
	hello(1, 2) // undefined 1 2
	hello.call(undefined, 1, 2) // undefined 1 2
	hello.apply(undefined, [1, 2]) // undefined 1 2
	```

- `bind`
	- `bind` 之後用 `call` 就沒用了
	```js
	'use strict';
	function hello() {
	  console.log(this)
	}
	
	const myHello = hello.bind('my')
	myHello.call('call') // my
	```

# `this` 的值
	this 的值與程式碼的位置沒有相關，僅與如何呼叫有關。
	判斷方式：把所有的 function call，都轉成利用 `call` 的形式來看。如下：

```js
const obj = {
  value: 1,
  hello: function() {
	console.log(this.value)
  }
}

obj.hello() // 1
obj.hello.call(obj) // 轉成 call
const hey = obj.hello
hey() // undefined
hey.call() // 轉成 call
```

```js
const obj = {
  value: 1,
  hello: function() {
    console.log(this.value)
  },
  inner: {
    value: 2,
    hello: function() {
      console.log(this.value)
    }
  }
}

const obj2 = obj.inner
const hello = obj.inner.hello
obj.inner.hello() // obj.inner.hello.call(obj.inner) => 2
obj2.hello() // obj2.hello.call(obj2) => 2
hello() // hello.call() => undefined
```

# 箭頭函式
	在宣告它的地方的 this 是什麼，它的 this 就是什麼:
```js
const obj = {
  x: 1,
  hello: function(){
    // 這邊印出來的 this 是什麼，test 的 this 就是什麼
    // 就是我說的：
    // 在宣告它的地方的 this 是什麼，test 的 this 就是什麼
    console.log(this)     
    const test = () => {
      console.log(this.x)
    }
    test()
  }
}

obj.hello() // 1
const hello = obj.hello
hello() // undefined
```

## 箭頭函式沒有權限取得 this, 除非在 function 當中
```js
const event = {
    name: 'Birthday Party',
    printGuestList: () => {
        console.log('Guest list for ' + this.name) // undefined
    }
}

event.printGuestList()
```

→ 可解決以下範例困境：以下範例在 forEach 中會變為 `function.call()`，所以會拿到 `undefined`，我們可以將 `function` 改為箭頭函式，使他能夠取得所在位置的 this 值
```js
const event = {
    name: 'Birthday Party',
    guestList: ['Andrew', 'Jen', 'Mike'],
    printGuestList() {
        console.log('Guest list for ' + this.name)
        
        this.guestList.forEach(function(guest) => {
            console.log(guest + ' is attending ' + this.name) // this.name is undefined
        })
    }
}

event.printGuestList()
```

→ 改寫為以下：
```js
const event = {
    name: 'Birthday Party',
    guestList: ['Andrew', 'Jen', 'Mike'],
    printGuestList() {
        console.log('Guest list for ' + this.name)
        
        this.guestList.forEach((guest) => {
            console.log(guest + ' is attending ' + this.name)
        })
    }
}

event.printGuestList()
```