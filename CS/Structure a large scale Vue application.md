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
- readme.md
	- 可以在每個 directory 當中，留下 readme.md，讓大家清楚該 directory 的作用為何。
- helpers
	- 類似 spiderman，放常常使用的函式、功能。
- layouts
	- 定義一些可重複使用的版面，裡面不會有內容，內容都是傳送進去的。
- plugins
	- 可以去做一些 plugins 的設定，簡單的可寫在 Index，複雜的就另外開 file import 進 index。
- globals.js
	- 可以去放一些 global 的變數、function 等...
	```js
	const app = createApp({})
	app.config.globalProperties.$http = () => {}
	```