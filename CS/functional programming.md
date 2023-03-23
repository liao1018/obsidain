#cs #clean-code

- be honsest to your function name
- no side effects function
	-  如果兩個 arrays 要合併，產生一個新 array 最好。

可預測、有利於 uni test

# Pure function
	same input, same output
 
- 對 Parmas 誠實，不會隨意使用外部變數
- no side effects
- 若要有 side effects ， 利用 monad 概念去實作。

# Immutability
- 變數不可變動，變動的話不好去預測
- 要去實現的話，迴圈幾乎就沒用了。
- 可以用一些高階函式代替掉遞迴

# Declarative
	直接告訴電腦要什麼