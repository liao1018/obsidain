#cs #web  #node 

# introduction
![[Pasted image 20220719140849.png]]
- Javascript is a programming language, usually , run on browser.
- browsers also use the v8 engine. node.js use v8 to compile js to machine code.
- node.js adds some feature on V8 by c++.

# node.js's role
- Run server
	- create server, listen to incoming request.
- Business logic
	- handle response, validate input, ...
- Response
	- return responses

# using REPL or using file
- REPL
	- read, evaluate, print, loop
	- when u type codes on terminal, you're in REPL
	```js
	> node // go into REPL
	```
- using file
	- real app

# Global Features vs Core Modules vs Third-Party Modules
-   Global Features
    -   like const, let…
-   Core Modules
    -   path, fs…
-   Third-Party Modules
    -   use npm install to install modules

[[node single thread, event loop]]
[[jwt]]
[[Emitter]]