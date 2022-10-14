#cs #js

---
# introduction
> 看變數的資料型別，決定傳遞行為是 Pass by value 或 Pass by reference 。

-   當變數的值是**原生型別(primitive)**時，是pass by value，包含
    -   String
    -   Number
    -   Boolean
    -   Undefined
    -   Null (註)
-   當變數的值是物件型別，是pass by reference，包含
    -   Array
    -   Object

# 然而，事情可以在清晰一點
> 事實上，Object 也是 pass by value，只是傳的是Object 本身的reference value。

EX: 
```javascript
function changeStuff(a, b, c)
{
  a = a * 10;
  b.item = "changed";
  c = {item: "changed"};
}

var num = 10;
var obj1 = {item: "unchanged"};
var obj2 = {item: "unchanged"};

changeStuff(num, obj1, obj2);

console.log(num); // 10
console.log(obj1.item); // changed
console.log(obj2.item); // unchanged
```
因為obj1 是pass by reference value，所以在函式內部會有一個變數存放該reference，這時候更改這個reference 上的物件的properties，就直接影響到Obj1。

但如果你是重新賦值，你就只是給了函式內部儲存的那個變數另外一個reference value，外面的Obj2 不受其影響。

# 應用
> 使用陣列實字 (Array Literals) 和物件實字 (Object Literals) 重新賦值

```js
/* array literals */
var ary1 = [1, 2, 3];
var ary2 = ary1;
console.log(ary1); // [1, 2, 3]
console.log(ary2); // [1, 2, 3]

ary1 = [99, 100];
console.log(ary1); // [99, 100]
console.log(ary2); // [1, 2, 3]


/* object literals */
var person1 = { money: 111 };
var person2 = person1;
console.log(person1);  // {money: 111}
console.log(person2);  // {money: 111}

person1 = { money: 222 };
console.log(person1);  // {money: 222}
console.log(person2);  // {money: 111}
```