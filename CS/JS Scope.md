#cs #js

# Introduction
	Scope 指變數可存取的範圍。每個變數都有自己的 Scope。
	詞彙環境(Lexical Environment)決定每個變數的 Scope，而 JS Engine 透過 Scope Chain 去尋找可用的變數。

# Lexical Scope
	與 Lexical Environment 不同，意思是執行程式的時候就會決定所有變數的 Scope，不會在執行過程中改變。