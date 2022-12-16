#cs #front-end #vue 

# Introduction
	v-bind 為 Vue 的單向綁定
	透過 (v-bind) + (@input 時去更改 value 的值)去實現雙向綁定。

# 修飾子
	以下 modifier can be chained together。
## v-model.lazy
-   沒有 lazy 的話，是在 input event 去 trigger 同步的。
-   加了 lazy 的話，是在 change event 去 trigger 同步。以input text 來說就是取消 focus 時，在某些情況會增加效率。

## v-model.number
	確保會被轉成 number，文件寫道如果該值不能被 parseFloat 轉換的話，會儲存最後一個合法的值。

## v-model.trim
	會把前後空格去掉。

# Custom component with v-model
```html
<custom-text-input v-model="value" />

<!-- IS THE SAME AS -->

<custom-text-input
   :modelValue="value"
   @update:modelValue="value = val"
/>
```

Vue3 內部還是要透過 computed 去寫，寫如何
```js
const value = computed({

get: () => props.modelValue,

set: (value) => emit('update:modelValue', val),

});
```