#cs #clean-code

打造更簡潔、可預測、有利於 unit test 的 code。
不需要過度 Follow，只需要了解好處，當作工具。

## 相關文章
[Ｍedium FP](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-functional-programming-7f218c68b3a0)
[10 Tips for Better Redux Architecture](https://medium.com/javascript-scene/10-tips-for-better-redux-architecture-69250425af44)
[Immutability](https://medium.com/javascript-scene/the-dao-of-immutability-9f91a70c88cd)
[Pure Function](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-pure-function-d1c076bec976)
[Function Composition](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-function-composition-20dfb109a1a0)

# 重要概念
- Pure functions
- Function composition
- Avoid shared state
- Avoid mutating state
- Avoid side effects
- monad
# Pure Function
	same input, same output
 
- 對 Parmas 誠實，不會隨意使用外部變數
- Has no side-effects

# Function Composition
	例如 f(g(x))，可以串起 function。

例如有一連串的 fliter，就會是上一個的結果當作下一個的參數。

# Avoid Shared State
## Shared State 問題
	可能 call 的順序不同會導致結果不同，會需要知道整個 state 的歷史。
正確範例：
```js
const x = {
	val: 2
};

const x1 = x => Object.assign({}, x, { val: x.val + 1});
const x2 = x => Object.assign({}, x, { val: x.val * 2});

console.log(x1(x2(x)).val); // 5

const y = {
	val: 2
};

x2(y);
x1(y);

console.log(x1(x2(y)).val); // 5
```

# Immutability
- 變數不可變動，變動的話不好去預測
- 要去實現的話，迴圈幾乎就沒用了。
- 可以用一些高階函式代替掉遞迴

## 實例
- js 裡面就是 const，但 const 如果是物件，可以去更改裡面的 properties。可以使用 Object.freeze() 去避免改變 properties，但仍無法阻止改變更深層的 Object。如果要實作，可以考慮 js library: immutable.js。

# Avoid Side Effects
Side effects 包括：
- Modifying any external variable or object property
- Logging to the console
- Writing to a file
- Writing to the network
- Triggering any external process

有副作用的話會利用 monads 做封裝，但 monads 概念太多，可以出一本書，可以慢慢了解。要知道的事是要獨立從邏輯中獨立出 side effects。這也是為何大多的前端框架會獨立出狀態管理的功能。

# Declarative
	直接告訴電腦要什麼

# Higher Order Functions
	Higher order function 是指把function 當參數或 return function 的 function
- Higher order function 幫助我們可以重複利用 function，達到 declarative。

# [[Tail Recursion]]