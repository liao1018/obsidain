#cs #web  #node 

是一個事件觸發器，可以去設定可被觸發的 function，程式範例如下：
```js
const EventEmitter = require('events');

// 建立一個新的 EventEmitter 實例
const myEmitter = new EventEmitter();

// 綁定一個 myEvent 事件的監聽器，接受一個參數
myEmitter.on('myEvent', (param1) => {
  console.log(`myEvent 觸發了，參數為 ${param1}`);
});

// 觸發 myEvent 事件並傳遞參數
myEmitter.emit('myEvent', 'hello');
```

