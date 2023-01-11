#cs #js


# proxy
[MDN 文章](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Proxy)

## Intro
	可以去自定義物件行為，可以去設定物件的 get, set 等 function，讓你在物件取值賦值可以自定義一些功能，像是取值給一些預設值，或是利用 set 去擋掉一些動作，使 Object 變為 read only。
```js
var p = new Proxy(target, handler);
```
`target`: The target object.

`handler`: An object whose properties are functions which define the behavior of the proxy when an operator is performed on it.

## ex: default value
	使 get 不到有一個預設值。
```js
let student1 = {
    age: 24,
    name: "Felix"
}

const handler = {
    get: function(obj, prop) {
        return obj[prop] ? obj[prop] : 'property does not exist';
    }
}

const proxy = new Proxy(student1, handler);
console.log(proxy.name); // Felix
console.log(proxy.age); // 24
console.log(proxy.class); // property does not exist
```

## ex: validation
```js
let student = {
    name: 'Jack',
    age: 24
}

const handler = {

    // get the object key and value
    get(obj, prop) {

    // check condition
    if (prop == 'name') {
      return obj[prop];
    } else {
      return 'Not allowed';
    }
  }
}

const proxy = new Proxy(student, handler);
console.log(proxy.name); // Jack
console.log(proxy.age); // Not allowed
```

## ex: read only object
```js
let student = {
    name: 'Jack',
    age: 23
}

const handler = {
    set: function (obj, prop, value) {
        if (obj[prop]) {
            
            // cannot change the student value
            console.log('Read only')
        }
    }
};

const proxy = new Proxy(student, handler);

proxy.name = 'John'; // Read only
proxy.age = 33; // Read only
```


# `in` 
	可以去 check Object & its prototype chain 有沒有該 key.
## EX
```js
const car = { make: 'Honda', model: 'Accord', year: 1998 };

console.log('make' in car);
// expected output: true
```

# Reassign Keys
	重複寫了兩次 key，會以下面寫到的為主。
```js
const obj = {
	a: 1,
	b: 2,
	c: 3,
	d: 4,
};
  
const obj2 = {
	...obj,
	a: 2,
}

console.log(obj2);
// { a: 2, b: 2, c: 3, d: 4 }
```