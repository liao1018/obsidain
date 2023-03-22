#cs #front-end #vue 

| 2.X Hooks    | 3.X Hooks      | 說明                                         |
| ------------ | -------------- | -------------------------------------------- |
| beforeCreate | setup()        | Vue 實體已建立，狀態與事件尚未初始化         |
| created      | setup()        | 狀態與事件已初始化(prop, data, computed,...) |
| beforeMount  | onBeforeMount  | Vue 實體尚未綁定到 DOM 節點                  |
| Mounted      | onMounted      | Vue 實體已經綁定到 DOM 節點                  |
| beforeUpdate | onBeforeUpdate | 狀態被更動，尚未同步到畫面前                 |
| updated      | onUpdated      | 同步到畫面上後                               | 

-   Created: 已經可以訪問數據，準備產生模板
    -   可進行全局插件安裝
-   BeforeMounted: 模板已經編譯完成渲染函數，準備掛載到 DOM
-   onmounted: 已掛載完成，可以去操作 DOM
-   unMounted: 完全被銷毀