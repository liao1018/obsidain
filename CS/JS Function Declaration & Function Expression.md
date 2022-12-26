#cs #js

[參考文章](https://www.freecodecamp.org/news/when-to-use-a-function-declarations-vs-a-function-expression-70f15152a0a0/)

# Introduction
## Function declaration
```js
function doStuff() {};
```
## Function expression
```js
const doStuff = function() {}
```

# Hoisting
	Function declarations are hoisted but function expressions are not.

# The case for function expression
	Function expressions 可以避免環境遭到污染，以下有一些案例會用到。
## [[IIFE]]
## Callback function