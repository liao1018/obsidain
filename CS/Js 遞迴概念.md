#cs #js

	遞迴函式會有一個中止條件，會持續往下帶入。

```js
//遞迴加法
function sumRecursion(num){
	// 邊界條件
    if( num == 1){
        return 1;
    }else{
        const Sn = sumRecursion(num-1)+num
        return Sn
    }
}

console.log('遞迴加法',sumRecursion(6)) // >>21
view raw Markdium-JavaScript.js hosted with ❤ by GitHub
```

→ 因為 stack 的緣故，會有下面的情況產生：(想像 stack 的概念)

```js
function sumRecursion(num){
    console.log('num : ' ,num)
    if( num == 1){
        console.log('num =1 ' ,num)
        return 1;
    }else{
        const sn = sumRecursion(num-1)+num
        console.log('sn ' , sn)
        return sn
    }
}

console.log(s(6))

>>>>
num :  6
num :  5
num :  4
num :  3
num :  2
num :  1
num =1  1
sn  3
sn  6
sn  10
sn  15
sn  21
21
view raw Markdium-JavaScript.js hosted with ❤ by GitHub
```