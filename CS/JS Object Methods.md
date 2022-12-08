#cs #js

# in operator
	可以去 check Object & its prototype chain 有沒有該 key.
## EX
```js
const car = { make: 'Honda', model: 'Accord', year: 1998 };

console.log('make' in car);
// expected output: true
```