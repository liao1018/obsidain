#mongoDb #database 

---
# 一些技巧操作
## bulkwrite
- 一次可以對資料庫進行多個動作
	- 應用：
		1. upsert 多筆不同資料(如果有就更新，沒有就新增)
			- 不能夠使用update many 的原因是每一筆要更新的資料不一樣
			EX: 每小時去撈當天的檢驗報告存到資料庫，因為每次撈的每一筆都要upsert，就是就可以使用bulkwrite
## update
- set 可以不用全部欄位列出，可以只 set 幾個欄位就好，剩下的不會給你亂動。
## aggrgate
[[aggregate]]

---
[[mongoDB  shell]]
[[mongoDB compass]]
[[mongoDB schema design]]

