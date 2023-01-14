#cs #front-end #vue 

# 基本使用方式
	可以套用 early return 的概念，讓複雜的 v-if/v-show 變得較為簡單易懂。

# v-show, v-if 對比
	v-show 是透過操作 CSS 的 display:none，v-if 是直接考慮要不要渲染 HTML DOM，若是更動頻率較大，用 v-show 效能較佳。若頻率小，有時甚至不需要 render 出來時，利用 v-if 就是較好的解法。

# 利用 v-show Filter 清單用
	有些時候，畫面清單要 show 哪些會透過你所選擇的去 filter，我們可以透過 v-show 去判斷該元件要不要 show 。