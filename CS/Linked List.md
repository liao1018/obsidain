#cs #data-type

# v.s. Array
## Array
- 優點
	- 因是連續記憶體，查詢方便，O(1)。
	- 省空間，不必花空間在 pointer 上。
- 缺點
	- 操作成本較高(塞元素進去 array 或是拿掉元素)，O(N)。

## Linked List
- 優點
	- 操作成本較低，更改 pointer 即可，O(1)。
- 缺點
	- 查詢成本較大，一定要從頭開始找，O(N)。
	- 空間需求較大，需存取 pointer。

# JS 範例
[ES6 實作& Leetcode 題目解析](https://medium.com/@nchuuu/linked-list-es6-javascript%E5%AF%A6%E4%BD%9C%E5%8F%8Aleet-code%E9%A1%8C%E7%9B%AE%E8%A7%A3%E6%9E%90-4afcd9a67b3d)
