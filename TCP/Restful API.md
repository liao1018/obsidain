#cs #web 

# Introduction 
	是一種設計風格，統一風格將 API 概念簡化。

 # 三個組成成分
	URL -> 對應唯一資源
	Method -> Http methods
	資料格式 -> json,...

# GET, POST 差別
GET 與 POST 均為常使用的 Http request methods，主要差別如下：

-   傳遞參數方式不同，GET 是透過 URL 的 query string 傳遞參數，而 post 是透過 request body 傳遞參數
-   安全性不同，因為傳遞參數的方式不同，對應安全性也就不同。GET 的參數會暴露在 URL 中，不適合傳遞重要資訊，例如密碼等。而 POST 則是隱藏在 request body 中，安全性較高
-   緩存機制不同，GET 請求通常會被瀏覽器緩存，在後續的請求中可能會使用緩存的資料；而 POST 請求不會被瀏覽器緩存，每次請求都會從服務端獲取最新的資料。

依照上述特性總結，GET 適合用於獲取資料、POST 適合用於提交資料。

# 好處
- 有唯一的 URL 表示資源位置且所有資源都用 URL 定位，不會受其他資源影響。
- Cache 機制：例如 Get 會有 Cache, 亦即 client 若向 Server 請求相同資源， 可以利用cache 機制減少 Requests 
	- 問題：// todo
		- 哪些 methods 有 cache?
		- cache 的運作原理
- Client-server 分離
	- 問題：// todo
		- 原本沒分離的原因？