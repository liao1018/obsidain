#cs #web  #node 

# introduction
![[Pasted image 20220909165948.png]]
- js 是single thread 的，任何需要等結果的callback 都丟到event loop。
- fs 則丟到worker pool 上，worker pool 上則是 different threads。

# event loop
- node event loop 與 js event loop 是不同的
- Node 在執行完 single thread 所有程式碼後，就會進入瘋狂event loop 循環。
![[Pasted image 20220909170622.png]]

### 六個macrotask queue (task queue) 
#### Timers
會被丟到這個queue 的是setTimeout(), setInterval() 計時器結束後，callback 會被丟進這個queue。

#### Pending callbacks
這個queue 是給作業系統層級使用的。

#### Idle, prepare
這個queue 是給內部使用，可以忽略。

#### Polling
當app 運行時有新的 I/O 資料進來可以被讀取，例如 .on('data', callback) 裡面的callback 就會被丟到這個queue。

#### Check
有一個關時間用的 setImmediate()，他callback 的queue 就在這。

#### Close callbacks
有關閉連線、檔案等等動作的操作，例如 socket.on('close', callback) ，只要是有關閉動作的callback 就會在這個queue。

以上六個是優先度較低的queue，有兩個優先度較高的queue。

### 另外兩個高優先層級的queue
#### nextTick Queue
優先層級最高，是在 process.nextTick() 裡面的 callback 都會來這。

#### microTask Queue
優先度次高，promise 的狀態轉為 resolve 或 reject 的時候，裡面的callback 就會跑到這個 queue。


# node js 解讀程式碼的順序
- 先把整份程式碼跑一次，遇到同步函式都當場處理。
- 該註冊的就當場註冊。不論是promise, async function, setTimeout 等等
- 程式碼跑完一遍後，Node js 就會跑到 event loop 循環了，瘋狂循環。
- 循環過程中若有 優先度更高的兩種 callback ，會優先處理，再跑回 event loop。
EX: 
```js
console.log('start');
 
process.nextTick(function() {
  console.log('nextTick1');
});
 
setTimeout(function() {
  console.log('setTimeout');
}, 0);
 
new Promise(function(resolve, reject) {
  console.log('promise');
  resolve('resolve');
}).then(function(result) {
  console.log('promise then');
});
 
(async function() {
  console.log('async');
})();
 
setImmediate(function() {
  console.log('setImmediate');
});
 
process.nextTick(function() {
  console.log('nextTick2');
});
 
console.log('end');
```
```
// result
start
promise
async
end
nextTick1
nextTick2
promise then
setTimeout
setImmediate
```