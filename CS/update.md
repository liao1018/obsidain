#cs #database #mongoDb

[參考文件](https://www.mongodb.com/docs/manual/reference/operator/update/positional-filtered/)

# 利用 `$[identifier]` 去 set nested array 中的東西
## Ex
	修改陣列中某些 element。
```js
db.students2.insertMany( [
   {
      "_id" : 1,
      "grades" : [
         { "grade" : 80, "mean" : 75, "std" : 6 },
         { "grade" : 85, "mean" : 90, "std" : 4 },
         { "grade" : 85, "mean" : 85, "std" : 6 }
      ]
   },
   {
      "_id" : 2,
      "grades" : [
         { "grade" : 90, "mean" : 75, "std" : 6 },
         { "grade" : 87, "mean" : 90, "std" : 3 },
         { "grade" : 85, "mean" : 85, "std" : 4 }
      ]
   }
] )
```
```js
db.students2.updateMany(
   { },
   { $set: { "grades.$[elem].mean" : 100 } },
   { arrayFilters: [ { "elem.grade": { $gte: 85 } } ] }
)
```
→ 更新所有的 document 當中 grades 中 grade 超過 85 當中的 mean。其中，elem 就是用來求哪些 index 的 grade 超過 85。

Result:
```js
{
   "_id" : 1,
   "grades" : [
      { "grade" : 80, "mean" : 75, "std" : 6 },
      { "grade" : 85, "mean" : 100, "std" : 4 },
      { "grade" : 85, "mean" : 100, "std" : 6 }
   ]
}
{
   "_id" : 2,
   "grades" : [
      { "grade" : 90, "mean" : 100, "std" : 6 },
      { "grade" : 87, "mean" : 100, "std" : 3 },
      { "grade" : 85, "mean" : 100, "std" : 4 }
   ]
}
```

## EX2 
	不一定要用 `$set`，像是可以用 `$inc`，並且 `arrayFilter` 可以多條件。
```js
db.students3.insertMany( [
   {
      "_id" : 1,
      "grades" : [
         { "grade" : 80, "mean" : 75, "std" : 6 },
         { "grade" : 85, "mean" : 100, "std" : 4 },
         { "grade" : 85, "mean" : 100, "std" : 6 }
      ]
   },
   {
      "_id" : 2,
      "grades" : [
         { "grade" : 90, "mean" : 100, "std" : 6 },
         { "grade" : 87, "mean" : 100, "std" : 3 },
         { "grade" : 85, "mean" : 100, "std" : 4 }
      ]
   }
] )
```
```js
db.students3.updateMany(
   { },
   { $inc: { "grades.$[elem].std" : -1 } },
   { arrayFilters: [ { "elem.grade": { $gte: 80 }, "elem.std": { $gt: 5 } } ] }
)
```
Result: 
```js
{  "_id" : 1,
   "grades" : [
      { "grade" : 80, "mean" : 75, "std" : 5 },
      { "grade" : 85, "mean" : 100, "std" : 4 },
      { "grade" : 85, "mean" : 100, "std" : 5 }
   ]
}
{
   "_id" : 2,
   "grades" : [
      { "grade" : 90, "mean" : 100, "std" : 5 },
      { "grade" : 87, "mean" : 100, "std" : 3 },
      { "grade" : 85, "mean" : 100, "std" : 4 }
   ]
}
```

## EX3
	`arrayFilter` 可以用其他運算子。
```js
db.alumni.insertMany( [
   {
      "_id": 1,
      "name": "Christine Franklin",
      "degrees": [
         { "level": "Master" },
         { "level": "Bachelor" }
      ],
  },
   {
      "_id": 2,
      "name": "Reyansh Sengupta",
      "degrees": [ { "level": "Bachelor" } ],
   }
] )
```
```js
db.alumni.updateMany(
   { },
   { $set : { "degrees.$[degree].gradcampaign" : 1 } },
   { arrayFilters : [ {"degree.level" : { $ne: "Bachelor" } } ] }
)
```
```js
 {
  _id: 1,
  name: 'Christine Franklin',
  degrees: [
     { level: 'Master', gradcampaign: 1 },
     { level: 'Bachelor' }
  ]
},
{
  _id: 2,
  name: 'Reyansh Sengupta',
  degrees: [ { level: 'Bachelor' } ]
}
```
## EX4
	利用 $[] 去選取陣列所有元素：
```js
db.students4.insertOne(
   { "_id" : 1,
      "grades" : [
        { type: "quiz", questions: [ 10, 8, 5 ] },
        { type: "quiz", questions: [ 8, 9, 6 ] },
        { type: "hw", questions: [ 5, 4, 3 ] },
        { type: "exam", questions: [ 25, 10, 23, 0 ] },
      ]
   }
)
```
```js
db.students4.updateMany(
   {},
   { $inc: { "grades.$[].questions.$[score]": 2 } },
   { arrayFilters: [  { "score": { $gte: 8 } } ] }
)
```
```js
{
   "_id" : 1,
   "grades" : [
      { "type" : "quiz", "questions" : [ 12, 10, 5 ] },
      { "type" : "quiz", "questions" : [ 10, 11, 6 ] },
      { "type" : "hw", "questions" : [ 5, 4, 3 ] },
      { "type" : "exam", "questions" : [ 27, 12, 25, 0 ] }
   ]
}
```