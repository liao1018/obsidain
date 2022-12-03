#cs #js

# Introduction
	顧名思義，就是變數被提升了。

# 為什麼需要 Hoisting
	讓 function 可以互相呼叫、可以不用都宣告在最上面。
	對於變數來說沒什麼好處。

# var 的 hoisting
	提前宣告但不會提前賦值。
```js
console.log(a) // undefined
var a = 5
```
可以想像成以下：
```js
var a
console.log(a) // undefined
a = 5
```

## 變數傳入相當於 var 宣告
```js
function test(v){
  console.log(v)
  var v = 3
}
test(10)
```
相當於：
```js
function test(v){
  var v = 10 // 因為下面呼叫 test(10)
  var v
  console.log(v)
  v = 3
}
test(10)
```

## function 宣告 > var 宣告
```js
console.log(a) //[Function: a]
var a
function a(){}
```

# let, const Hoisting
	理論上來說不會 Hoisting
```js
console.log(a) // ReferenceError: a is not defined
let a
```
## 但在一些情況有點奇怪
```js
var a = 10
function test(){
  console.log(a)
  let a
}
test() //ReferenceError: a is not defined
```
→ 如果完全沒有提升，應該是要 10 才對

# Hoisting 運作原理
	進入 function 的時候，會產生一個 Execution Context(EC)，裡面存放執行 Function 所需資訊，EC 會有想對應的 Variable Object(VO)。裡面存放以下東西：
	1. Function 及其內容。
	2. 傳入的參數名稱及值。
	3. var 變數名稱並設置為 undefined。
	Note: 
		1. 如果有重複，以 function 為第一優先。
		2. 直到執行到內部程式碼 var 部分才會被賦值。

 # JS 是直譯式語言，但仍然會經過編譯過程
	 編譯過程：把各個 Scope 的變數資訊放入 VO。
	 執行過程：如果有賦值或是取值到 VO 去找，有必要會沿著 Scope Chain 去找。