#cs #front-end #vue 

# Introduction
	是一個插槽，可以把 HTML 插到裡面。可用在 modal 之類的用法，用法如下：

```html
<!-- Card.vue 組件模板 -->
<template>
  <div class="card">
    <h2>{{ title }}</h2>
    <div class="card-body">
      <slot></slot>
    </div>
  </div>
</template>
```
```html
<!-- App.vue 父組件模板 -->
<template>
  <div>
    <Card title="標題">
      <p>這是一段內容</p>
    </Card>
  </div>
</template>
```

# 多段內容需要插入時
	可利用命名的方式，插入不同內容。

```html
<!-- Card.vue 組件模板 -->
<template>
  <div class="card">
    <div class="header">
      <slot name="header"></slot>
    </div>
    <div class="content">
      <slot></slot>
    </div>
    <div class="footer">
      <slot name="footer"></slot>
    </div>
  </div>
</template>
```

父元件有兩種語法 `<template v-slot:header>` 或是 `<template #header>`
```html
<!-- App.vue 父組件模板 -->
<template>
  <card>
    <template #header>
      <h2>Card Title</h2>
    </template>
    <p>Card Content</p>
    <template #footer>
      <small>Card Footer</small>
    </template>
  </card>
</template>
```