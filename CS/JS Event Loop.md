#cs #js

# Introduction
	JS 的運行環境 (Runtime) 是單執行緒(Single Thread)，意思是一次只能執行一段程式碼。但可以去 Trigger 瀏覽器 WebAPIs(DOM, XMLHttpRequest, setTimeout,...)，Trigger 時不會影響到 JS Runtime，Event Loop 就是控制這些事件的流程。

# 說明 Event Loop
![[Pasted image 20221226130139.png]]
- Heap
	- 宣告變數、函式的儲存位置。
- Stack
	- 函式執行時會堆進來(pop in)，執行結束會(pop out)，最下面會是 main 函式。
- WebAPIs
	- 瀏覽器提供的方法，執行結束的 Callback function 會丟到 Callback queue 去排隊(先進先出)。
- Callback queue
	- 會等到 Stack 空掉的時候才會去被丟到 Stack 去執行。
- Event Loop
	- 持續查看 Stack 空了沒有，空了就從 Callback Queue 丟__一個__任務進來。
