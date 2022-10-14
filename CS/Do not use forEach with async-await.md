#cs #js

參考文章
Promise.all 使用機制
https://gist.github.com/joeytwiddle/37d2085425c049629b80956d3c618971 
Promise.allSettled 例外處理 
https://stackoverflow.com/questions/30362733/handling-errors-in-promise-all

---

# foreach 不要使用async function
- 因為foreach 前面不能加await ，因為foreach 不是一個promise，所以不會等foreach 跑完才跑到下一段code
	```js
	const players = await this.getWinners();

	// BAD
	await players.forEach(async (player) => {
	  await givePrizeToPlayer(player);
	});
	
	await sendEmailToAdmin('All prizes awarded');
	```
-> 不會await forEach，會直接執行 sendEmailToAdmin
- 第二個原因是foreach 沒有順序性，等同於把所有 async 丟到 callback。不過有時候我們確實不在乎

## 解法
- 不在意順序的話可使用 Promise.all , Promise.allSettled，其中 Promise.allSettled 可以回傳每一個請求是否成功，較為清楚(參考第二篇文章)。而 Promise.all 只要有錯誤就會回傳錯誤並暫停其他。
	- Promise.allSettled會確保陣列中每一個 async function, promise 都得到結果，會接收他們的 return 作為 Promise.allSettled 的 return.value 值，並且 return.status 會顯示是否成功。e.g. 
	- Promise.allSettled 裡面放 Promise 的寫法
	```js
	Promise.allSettled([
	  Promise.resolve(33),
	  new Promise((resolve) => setTimeout(() => resolve(66), 0)),
	  99,
	  Promise.reject(new Error('an error'))
	])
	.then((values) => console.log(values));
	
	// [
	//   {status: "fulfilled", value: 33},
	//   {status: "fulfilled", value: 66},
	//   {status: "fulfilled", value: 99},
	//   {status: "rejected",  reason: Error: an error}
	// ]
	```
	- Promise.allSettled 配合 async-await 的寫法
	```js
	const values = await Promise.allSettled(players.map(async (player) => {
	  const result = await givePrizeToPlayer(player);

	  return { result }
	}));
	
	// [
	//   {status: "fulfilled", value: { result: 1 }},
	//    ...
	// ]
	```
- 在意順序的話可以使用for(...of...), reduce (參考第一篇文章)
	```js
	for (const player of players) {
	  await givePrizeToPlayer(player);
	}
	```	
	
	```js
	await players.reduce(async (a, player) => {
	  // Wait for the previous item to finish processing
	  await a;
	  // Process this item
	  await givePrizeToPlayer(player);
	}, Promise.resolve());
	```

## 結論
遇到需要在意順序的 async function，使用 for 或是 reduce。
遇到不需要在意順序的 async function，使用 Promise.allSettled 配合 Array.map