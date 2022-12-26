#cs #js

# 比較
| 宣告      | scope          | 可否重複宣告 |
| --------- | -------------- | ------------ |
| let const | block scope    | 不可，會錯誤 |
| var       | function scope | 可，後蓋前   | 

# const 的 immutable
	const 意思是常數，但是如果宣告的是一個物件或是陣列，是可以更改裡面的值的。
	原因：物件跟陣列只是一段地址，只改變裡面的值不會改變地址，所以 const 依然認為是沒有改變的。