 #cs #database #mongoDb

## Aggregation Pipeline Example
aggregate 裡面分stage，每一個stage裡面做一次filter, group...，就像pipeline(管道)一樣
```js
db.orders.aggregate( [

// Stage 1: Filter pizza order documents by pizza size

{

$match: { size: "medium" }

},

// Stage 2: Group remaining documents by pizza name and calculate total quantity

{

$group: { _id: "$name", totalQuantity: { $sum: "$quantity" } }

}

] )
```
- 第一階段是 先把size 是 medium 的filter 出來
- 第二階段是透過name 把所有的name group 成一個(這時候_id 就會是name)，然後把quantity 加總起來儲存在totalQuanlity 裏面

## match 
filter 的概念 

## group
將多個 document group 成一個，利用 id

## out
只能加在一串 pipeline 的最後，用來輸出到另一個 collection。
如果 collection 已經存在，會取代原本的 collection。
→ 可以在需要將 document 的一部份分割出來成為新 collection的時候使用。

## lookup
	用來利用 local 欄位去找尋其他 collection 的欄位用。
	例如 members 底下的 appointments 只會存 _id，需要 appointments 詳細資料就要用 local 的 _id 欄位去 collection appointments 中搜尋。

# 例子們
## sort 依照特定規則
	addFields 新增欄位賦予權重，利用權重去 sort，最後再用 project 把產生的欄位去除。