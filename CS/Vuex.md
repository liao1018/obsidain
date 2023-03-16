#cs #front-end #vue 

# Introduction
	在 Vue 當中不可能都利用 props 與 emit 進行元件溝通。
- 單一資料來源原則
	- 來源單一，才不會有 Debug 時不知是哪裡出問題。
- 單向資料流
	- 來源單一後，傳進組建的方向也要單一，才會是 修改 -> 使用 的順序