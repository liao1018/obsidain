#cypto 

# Introduction  
- every hash value has the same length.
- hash values are numerical value.
- 兩個些微不同的input 會產生不同output（極低機率相同）
- The same input generate the same output.
- There are different algorithms. e.g. md5, SHA1, ...
- If we only have output, we can’t calculate it into one input.

# 應用
## 作為密碼儲存欄位
可以利用雜湊的單方向性作為密碼的儲存欄位。解出來為相同雜湊值才可以通過驗證，這樣就必定會經過後端程式驗證，且保證密碼安全性。