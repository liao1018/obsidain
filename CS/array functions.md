#cs #js

# Array.prototype.filter()
## 特別用法：要 filter 非空的欄位
```js
analyses = analyses.filter((analysis) => (
(dept ? analysis.member.dept === dept : true)
&& (room ? analysis.member.room === room : true)
&& (dr ? analysis.member.dr === dr : true)
));
```
-> 利用邏輯精簡化。

# Array.prototype.every()
```js
const isBelowThreshold = (currentValue) => currentValue < 40;

const array1 = [1, 30, 39, 29, 10, 13];

console.log(array1.every(isBelowThreshold));
// true
```

[[Do not use forEach with async-await]]
[[Js Sort]]