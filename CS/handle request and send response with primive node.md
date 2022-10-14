#cs #web  #node 

# understanding request
- request has a bunch of data, we can take some important parts of it.
```js
const http = require('http');

const server = http.createServer((req, res)=>{
    console.log('req.url', req.url);
    console.log('req.method', req.method);
    console.log('req.headers', req.headers);
});

server.listen(3000);
```
![[Pasted image 20220904144134.png]]
-> req.url 是 http://localhost:3000 後面的，所以只有 /

# sending response
```js
const http = require('http');

const server = http.createServer((req, res)=>{
    console.log('req.url', req.url);
    console.log('req.method', req.method);
    console.log('req.headers', req.headers);

    res.setHeader('Content-Type', 'text/html');
    res.write('<html>');
    res.write('<head><title>My Title</title></head>');
    res.write('<body><h1>My H1</h1><body>');
    res.write('</html>');
    res.end();
});

server.listen(3000);
```
- res.end() 代表要回傳給client了，之後就不能在write了

### using dev tool to observe details of req/res.
> dev tool -> network  -> 有一個request list -> 去看要看哪一個request.
- 除了我們設定的Header 以外，response 會有其他預設的Headers
- 以下網址提供overview of http headers and their roles.
	- https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers 

# handle different routes of request
```js
const http = require('http');
const fs = require('fs');

const server = http.createServer((req, res)=>{
    const { url, method } = req;
    console.log(url, method);

    if (url === '/') {
        res.setHeader('Content-Type', 'text/html');
        res.write('<html>');
        res.write('<head><title>Enter Message</title></head>');
        res.write(`
        <body>
	        <form action="/message" method="POST">
		        <input type="text" name="message">
		        <button type="submit">Send</button>
	        </form>
        <body>`);
        res.write('</html>');
        res.end();
        return;
    }

    if (url === "/message" && method === "POST") {
        // 之後再真的去抓what client type
        fs.writeFileSync('message.txt', 'Dummy');
        // 代表redirect
        res.statusCode = 302;
        // 一定要在特定的status code下，才能順利透過Location 去redirect
        res.setHeader('Location', '/');
        res.end();
        return;
    }

    res.setHeader('Content-Type', 'text/html');
    res.write('<html>');
    res.write('<head><title>My Title</title></head>');
    res.write('<body><h1>My H1</h1><body>');
    res.write('</html>');
    res.end();
});

server.listen(3000);
```
- 處理完一個resquest 最後記得return. 
- about form tag
	- action: path
	- method: http method
- about input tag
	- using name to define name of key.
- res.statusCode 
	- 特定的status code 才能順利地透過Location 這個Header 去redirect.

# parsing request bodies
- In fact, a request is a stream of data, but we can listen to events to deal with it.
- We can save time by registering event listeners. However, remember that callback functions don't execute immediately. 
```js
const http = require('http');
const fs = require('fs');

const server = http.createServer((req, res)=>{
    const { url, method } = req;

    if (url === '/') {
        res.setHeader('Content-Type', 'text/html');
        res.write('<html>');
        res.write('<head><title>Enter Message</title></head>');
        res.write(`
        <body>
	        <form action="/message" method="POST">
		        <input type="text" name="message">
		        <button type="submit">Send</button>
	        </form>
        <body>`);
        res.write('</html>');
        res.end();
        return;
    }

    if (url === "/message" && method === "POST") {
        const body = [];
        req.on('data', (chunk) => {
            // chunk 是以buffer 形式儲存，若console 會轉成hex 的形式表達，但事實上還是二進位儲存。
            console.log(chunk); // <Buffer 6d 65 73 73 61 67 65 3d 61 70 70 6c 65>
            console.log(chunk.toString('hex'));// 6d6573736167653d6170706c65
            body.push(chunk);
        });
        // return early to avoid that the code execute below.
        return req.on('end', () => {
            // Buffer.concat 傳入 array，輸出一個連接後的buffer
            const parsedBody = Buffer.concat(body).toString();
            console.log(parsedBody); // message=apple
            const message = parsedBody.split('=')[1];

			// never block your code& ensure that the response end after finishing the file.
		    fs.writeFile('message.txt', message, (err) => { 
			    res.statusCode = 302;
			    res.setHeader('Location', '/');
			    res.end(); 
		    });
        });
    }

    res.setHeader('Content-Type', 'text/html');
    res.write('<html>');
    res.write('<head><title>My Title</title></head>');
    res.write('<body><h1>My H1</h1><body>');
    res.write('</html>');
    res.end();
});

server.listen(3000);
```
- The data we receive is binary data. If we console that, it will convert into hexadecimal.
- Return early to avoid the code run below.
- WriteFile makes our code non-blocking.
- To ensure that the response end after finishing the file, we register it in the callback of writeFile block.