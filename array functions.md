#js 

# filter
## 特別用法：要 filter 非空的欄位
```js
analyses = analyses.filter((analysis) => (
(dept ? analysis.member.dept === dept : true)
&& (room ? analysis.member.room === room : true)
&& (dr ? analysis.member.dr === dr : true)
));
```
-> 利用邏輯精簡化。

[[Do not use forEach with async-await]]