#node 

## creating a node server
```js
const http = require('http');

const server = http.createServer((req, res)=>{
    console.log(req);
});

server.listen(3000);
```
- http is core module of node js.
- http.createServer 傳入的參數可以去看document.

### 運作原理
![[Pasted image 20220904142438.png]]
- 可利用process.exit() 跳出event loop 
```js
const http = require('http');

const server = http.createServer((req, res)=>{
    console.log(req);
	process.exit(1);
});

server.listen(3000);
```
-> 通常0 代表success. 其他不同的數字代表不同的錯誤

[[handle request and send response with primive node]]