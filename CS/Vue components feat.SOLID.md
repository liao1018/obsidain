#cs #front-end #vue 

# Build Reusable Vue Component
	Component 內部只需要要求外部最少的資料，傳入資料 depend on Component 的設計。此外，在參考 SOLID 架構，打造更 maintainable 的 component。

# SRP
	一個組件負責一件事
```js
<template>
  <div>
    <ProductList :products="products" @product-selected="handleProductSelected" />
    <ProductFilter :categories="categories" @category-selected="handleCategorySelected" />
    <ProductDetail v-if="selectedProduct" :product="selectedProduct" />
  </div>
</template>

<script setup>
import { ref } from "vue";

const products = ref([])
const categories = ref([])
const selectedProduct = ref(null)

const handleProductSelected = (product) => {
  selectedProduct.value = product;
};

const handleCategorySelected = (category) => {
  // Filter products by category
};
</script>
```

# OCP
	Open for extension, close for modification.
假設一個情景，你有一個 List 組件、一組資料，今天你想要加上 sorting feature，可以如何實作去符合呢？
```js
// List.vue
<template>
  <ul>
    <li v-for="item in items" :key="item.id">{{ item.text }}</li>
  </ul>
</template>

<script setup>
defineProps({
  items: Array
})
</script>
```
```js
// Outside.vue
<template>
  <div>
    <button @click="toggleSortOrder">Toggle sort order</button>
    <List :items="sortedItems"/>
  </div>
</template>

<script setup>
import useSorting from './useSorting.js'

const { sortOrder, sortedItems, toggleSortOrder } = useSorting()

const items: [
  { id: 1, text: 'Item 1' },
  { id: 2, text: 'Item 2' },
  { id: 3, text: 'Item 3' }
]
</script>
```
```js
//composable.js
import { ref, onMounted } from 'vue'

export default function useSorting () {
  const sortOrder = ref('ascending')
  const sortedItems = ref([])
  
  function toggleSortOrder () {
    sortOrder.value = sortOrder.value === 'ascending' ? 'descending' : 'ascending'
  }

  onMounted(() => {
    sortedItems.value = items.value.sort((a, b) => {
      if (sortOrder.value === 'ascending') {
        return a.text.localeCompare(b.text)
      } else {
        return b.text.localeCompare(a.text)
      }
    })
  })
}
```
	其他例子：後端會去區分 串接廠商部分(close)->院所客製設定(open)。例如要門診表，會先經過 vendor 要到門診表，再進去 clinic 做客製化門診修改。這就符合 OCP。

# LSP
	子型態針對父型態進行設計，且子型態抽換不影響父型態功能。也可以視為，先去思考最後要怎麼去使用，讓子型態能夠符合父型態的規範。
- Vue 中概念相當於 component 當中的 slot.
```js
<template>
  <Form>
    <input type="text" v-model="username" />
    <input type="text" v-model="password" />
  </Form>
</template>

<script setup>
const username = ref('')
const password = ref('')
</script>
```
```js
<template>
  <form @submit.prevent="submit">
    <slot />
    <button type="submit">Submit</button>
  </form>
</template>

<script setup>
function submit() {
  console.log('Form submitted!')
}
</script>
```
	其他例子： 驗證程式碼(父型態: validate, 子型態: rules)
```js
import moment from 'moment-timezone';

const validators = {
  date: {
    method: (val) => moment(val, ['YYYYMMDD', 'YYYY-MM-DD'], true).isValid(),
    message: (chinese) => `${chinese}格式錯誤，請輸入8碼西元年月日。`,
  },
  mobile: {
    method: (val) => val && val.match(/^09\d{8}$/i),
    message: (chinese) => `${chinese}格式錯誤，請輸入09開頭共10位數字。`,
  },
  nonEmpty: {
    method: (val) => !!val,
    message: (chinese) => `請輸入您的${chinese}。`,
  },
  number: {
    method: (val) => !Number.isNaN(parseFloat(val)),
    message: (chinese) => `很抱歉，${chinese}必須是數字。`,
  },
  twid: {
    method: (val) => val && val.match(/^[A-Z]{1,2}\d{8,9}$/i),
    message: (chinese) => `很抱歉，${chinese}格式錯誤，請輸入1~2碼大寫英文字與8~9位數字。`,
  },
};

function validate({ form, rules }) {
  Object.entries(form).forEach(([key, value]) => {
    const rule = rules.find(({ field }) => field === key);
    if (!rule) return;

    const { chinese, type } = rule;
    if (!(validators[type].method)(value)) {
      throw Error(
        (validators[type].message)(chinese),
      );
    }
  });
}

export default {
  validate,
  memberInfo(form) {
    const rules = [
      { field: 'name', chinese: '姓名', type: 'nonEmpty' },
      { field: 'twid', chinese: '身分證字號', type: 'twid' },
      { field: 'birthdate', chinese: '生日', type: 'date' },
      { field: 'mobile', chinese: '手機號碼', type: 'mobile' },
    ];
    validate({ form, rules });
  },
  feedback(form) {
    const rules = [
      { field: 'name', chinese: '姓名', type: 'nonEmpty' },
      { field: 'mobile', chinese: '手機號碼', type: 'mobile' },
      { field: 'content', chinese: '意見回饋', type: 'nonEmpty' },
    ];
    validate({ form, rules });
  },
};
```

# ISP
	讓interface 分割，可以最小的滿足需求。不要做一個大的 Interface 去滿足多個需求。
```js
<template>
  <div>
    <Filter @change="setFilter" />
    <List :items="filteredItems" @select="selectItem" />
    <ItemDetail v-if="selectedItem" :item="selectedItem" @close="deselectItem" />
  </div>
</template>

<script setup>
import { reactive, toRefs } from 'vue'

const state = reactive({
  items: [...], // an array of items
  filter: '',
  selectedItem: null
})

const filteredItems = computed(() => {
  return state.items.filter(item => item.name.includes(state.filter))
})

function setFilter(filter) {
  state.filter = filter
}

function selectItem(item) {
  state.selectedItem = item
}

function deselectItem() {
  state.selectedItem = null
}

const { items, filter, selectedItem } = toRefs(state)
</script>
```

# DIP
	強調低耦合性，細節要依賴於抽象化，兩邊互相獨立。像是前後端之於 API，組件之間之於 props．