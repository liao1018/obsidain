#cs #js

# Introduction
	如果 return 一個 function 內有用到變數，變數便無法進行釋放。以下為閉包實作：

# EX
```js
function createCounter(name) {
  var count = 0;
  return function () {
    count++;
    console.log(count + ' ' + name);
  };
}

const dogCounter = createCounter('dog');
const catCounter = createCounter('cat');
const birdCounter = createCounter('bird');

dogCounter(); // 1 dog
dogCounter(); // 2 dog
catCounter(); // 1 cat
catCounter(); // 2 cat
birdCounter(); // 1 bird
dogCounter(); // 3 dog
catCounter(); // 3 cat
```

# ES5 閉包解決方案
```js
var btn = document.querySelectorAll('button')
for(var i=0; i<=4; i++) {
  btn[i].addEventListener('click', function() {
    alert(i)
  })
}
// 全部 i 都會是 5
```

## solution 1
```js
function getAlert(num) {
  return function() {
    alert(num)
  }
}
for(var i=0; i<=4; i++) {
  btn[i].addEventListener('click', getAlert(i))
}
```

## solution 2
```js
for(let i=0; i<=4; i++) {
  btn[i].addEventListener('click', function() {
    alert(i)
  })
}
```
