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
