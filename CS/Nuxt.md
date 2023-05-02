#cs #front-end #vue 

# Introduction
-   可以用npm 建立專案
-   Nuxt2 使用的是 Vue2，nuxt3 使用 vite& vue3，但目前在beta 階段
-   Nuxt 一些 function 支援 context，可以取出一些實用的東西。例如 function asyncData
-   Nuxt 內建 layout 的 feature
-   SSR
    -   送 request ，Nuxt 產生 html 給他（透過你寫的 function:asyn data…)。browser 端如果 route，就不會重新觸發 server，除非 hard refresh.