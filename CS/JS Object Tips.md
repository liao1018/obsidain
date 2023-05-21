#cs #js

# 選擇性加入 Key
解構+三元運算
```js
const obj = { oldKey: 'oldValue' };
const condition = true;
const newKey = 'newKey';
const value = 'value';

const newObj = {
  ...obj,
  ...(condition ? { [newKey]: value } : {})
};

console.log(newObj);
// Output: { oldKey: 'oldValue', newKey: 'value' }

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