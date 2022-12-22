#cs #front-end #vue 

| 2.X Hooks    | 3.X Hooks      | 說明                                         |
| ------------ | -------------- | -------------------------------------------- |
| beforeCreate | setup()        | Vue 實體已建立，狀態與事件尚未初始化         |
| created      | setup()        | 狀態與事件已初始化(prop, data, computed,...) |
| beforeMount  | onBeforeMount  | Vue 實體尚未綁定到 DOM 節點                  |
| Mounted      | onMounted      | Vue 實體已經綁定到 DOM 節點                  |
| beforeUpdate | onBeforeUpdate | 狀態被更動，尚未同步到畫面前                 |
| updated      | onUpdated      | 同步到畫面上後                               | 

