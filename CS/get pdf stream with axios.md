#cs #js

正常如果是可以透過瀏覽器打開的 pdf ，我們用 get 會得到 Content-Type: application/pdf 的 response。如果我們利用 axios 去設定 responseType: stream，可以得到二進位的的 data ，可以透過他來上傳至 s3。
```js
const stream = await spiderman.axios.get(url, {
      responseType: 'stream',
    });
```