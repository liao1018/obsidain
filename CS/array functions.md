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
	會去測試是否每一個元素就通過測試，如果有人沒通過，就會跳出迴圈並回傳 false。
```js
const isBelowThreshold = (currentValue) => currentValue < 40;

const array1 = [1, 30, 39, 29, 10, 13];

console.log(array1.every(isBelowThreshold));
// true
```
	可以用在跳出迴圈：
```js
nums.every((num, idx)=>{
	const diff = target - num;
	if(map[diff] !== undefined) {
		answer = [map[diff], idx];
		// 跳出迴圈
		return false;
	}

	map[num] = idx;
	return true;
})
```

# Array.prototype.some()
	一些通過測試即可

# Array.prototype.flatMap()
	相當於先 map
```js
const test = [
        {
            name: 'A',
            appointments: ['a', 'b', 'c', 'd'],
        },
        {
            name: 'B',
            appointments: ['e', 'f', 'g', 'h'],
        },
    ]
	.flatMap(({ appointments }) => appointments);

console.log(test);
// [
  'a', 'b', 'c',
  'd', 'e', 'f',
  'g', 'h'
]
```

與下列是等價的：

```js
const test = [
        {
            name: 'A',
            appointments: ['a', 'b', 'c', 'd'],
        },
        {
            name: 'B',
            appointments: ['e', 'f', 'g', 'h'],
        },
    ]
    .map(({ appointments }) => appointments)
    // [['a', 'b', 'c', 'd'],['e', 'f', 'g', 'h']]
    .flat();

console.log(test);
// [
  'a', 'b', 'c',
  'd', 'e', 'f',
  'g', 'h'
]
```

[[Do not use forEach with async-await]]
[[Js Sort]]
