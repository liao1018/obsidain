#cs #js 

[Js Sort 參考 medium 文章](https://medium.com/@leokao0726/%E6%B7%BA%E8%AB%87-js-sort-%E5%88%B0%E8%83%8C%E5%BE%8C%E6%8E%92%E5%BA%8F%E6%96%B9%E6%B3%95-1035f5b8cde8)

# Algorithms
	一般利用 Quick Sort，Length < 10 的時候利用 Insertion Sort。

- Quick Sort : [點我](https://www.youtube.com/watch?v=5nXrEBhBFpU) | Insertion Sort : [點我](https://www.youtube.com/watch?v=DfloPvgptJA)

# Sorting String → localeCompare
[MDN localeCompare 參考文章](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/localeCompare)

	可以利用不同國家的語言去 Sort 不同的字串，也可以客製不同的規則，例如需要比對字串又要比對數字時。

# Sorting 技巧
	當遇到不同條件的 Items 權重排序的不同，可以利用新增來為去計算權重值。

## 舉例 (housekeeping lambda app beds get)
想要以下優先順序：
1. 未打掃的放最上面
2. 按照院區排列
3. 院區內按照床號排列

解法：
1. 先 Sorting 床號，因為涉及文字及數字，會用到 localeCompare。
2. 新增權重用欄位。
3. 未打掃的權重 + 100
4. 依照不同優先順序的院所，依序是 +30 +20 +10 權重。
5. Sorting 權重欄位。