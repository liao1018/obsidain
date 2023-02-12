#cs #front-end #vue 

# Introduction
	最重要的一點是，可預測性(predictability)。為了達成此目標，可以去遵循一些標準，提高可預測性。

# Style Guide
[官方文件](https://vuejs.org/#rule-categories)
	按照原先架構是個好選擇，在此基礎上，加上自己的東西。

## Component Recommended Rules
- PascalCase filename.
- Global components 可以用相同的字首，EX: AppModal, TheHeader.
- Compoent names should not conflict with existing HTML words.

# Personal/Team Guide
- A flat component directory
	- 方便分類
	- 不用去想如何引用
	![[Pasted image 20230125171124.png]]
- Route/Page
	![[Pasted image 20230125171205.png]]

# Comprehensive File Structure
	介紹一些可以放進專案中的 directory。
## 結構
```
src
--assets
--components
--helpers
--layouts
--middlewares
--modules
--plugins
--router
--services
--static
--store
--views
```

## 介紹
- readme.md
	- 可以在每個 directory 當中，留下 readme.md，讓大家清楚該 directory 的作用為何。
- assets
	- fonts, images,icons, styles,…
- helpers
	- 類似 spiderman，放常常使用的函式、功能。
- layouts
	- 定義一些可重複使用的版面，裡面不會有內容，內容都是傳送進去的。
	- 利用 Slot，靜態的方式會導致切換不同 route 也會重新載入 Layouts，可透過動態去解決。
	- 有動態 layouts 的方式，可以去查詢
- Middlewares
	- work with router
	```js
		import Router from 'vue-router'
		import checkAuth from '../middlewares/checkAuth.js'
		const isAuthenticated = true
		const router = new Router({
		  routes: [],
		  mode: 'history'
		})
		router.beforeEach((to, from, next) => {
		  checkAuth(next, isAuthenticated)
		});
	```
- modules
	views 是進入點，modules 就是存放進入點之後可能會做的事，檔案結構會與 views 相對應，ex:
	-   an inner components' folder where you can save your vue components
	-   tests folder (I prefer to keep all related tests in the module)
	-   store.ts or store directory, where you keep your store module
	-   other files related to this module. It could be helper functions related only to the module.
	```
	src  
	--modules  
	----orders  
	------__tests__  
	------components  
	--------OrdersList.vue  
	--------OrderDetails.vue  
	------store  
	--------actions.ts  
	--------getters.ts  
	--------mutations.ts  
	--------state.ts  
	------helpers.ts  
	------types.ts
	```
- plugins
	- 可以去做一些 plugins 的設定，簡單的可寫在 Index，複雜的就另外開 file import 進 index。
	```js
	import MyPlugin from './myPlugin.ts'
	Vue.use(MyPlugin, { someOption: true })
	```
- services
	- 放 services，例如 API 相關等等
- static
	- 假資料
- store
	- 只會放 root 相關的，其他會藉由 modules 引入
- globals.js
	- 可以去放一些 global 的變數、function 等...
	```js
	const app = createApp({})
	app.config.globalProperties.$http = () => {}
	```
- views
	純粹放進入點，會與 modules 相對應，有以下好處：
	- more clear files structures
	- easy to understand which file is root on the page and where it starts to work