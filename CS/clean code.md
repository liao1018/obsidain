#cs #clean-code

# Guide Line
	訂出 Guide Line ，讓開發有跡可循。
- 規範可以參考 RFC 2119
    - MUST
    - MUST NOT
    - SHOULD
    - SHOULD NOT
    - MAY

# 文件
多寫文件，只要他人可能會不知道怎麼使用的時候。

# Code 的重點
1. Correctness
2. Well-designed
3. Well-styled

# 原則
> Clean code → Readable code


## 註解
- 可以加上前綴
- 註解的用意是將複雜度隱藏起來，將概念抽象化，讓開發者可以不用去管內部細節。
- 應該要寫程式碼的目的、為什麼要這樣寫。而不是程式碼在做什麼
- 在程式碼中不顯而易見的可寫註解
- 可以嘗試解釋看看自己的 code，不清楚的地方可以補註解
- 寫註解與寫程式本身同樣重要

## 減少互相耦合的機會

## Better Naming
- Variable name should tell their types.
-
## Don’t Repeat Yourself!(DRY)

## Single Responsibility Principle
- One purpose functions compose one multiple purposes function.
- 可以有一個做統合
```js
	const logSignup(email) => Log.add(new Date(), "signed up", email)

	async function signupUser(email) {
	createUser(email)
	notifyUser(email)
	logSignup(email)
	}
	
	async function createUser(email) {
	const user = await User.create({ email });
	await user.save();
	
	}
	
	async function notifyUser(email) {
	const notifcation = await Notification.create({ email });
	await notifcation.save();
	}
	
```

## Recursion Can Be More Concise
```js
//recursion
const stepsToHundred = (number, steps) =>
number < 100 ? stepsToHundred(number * 2, steps + 1) : steps

//iteration
const stepsToHundred = (number) => {

	let steps = 0
	
	while(number < 100) {
		number *= 2
		steps++
	}
	
	return steps

}
```

## Use Guard Clauses to Avoid Deep Nesting
```js
const getUSTime = (time) => {
	if(time <= 12) return time + "AM"
	return time + "PM"
}
```

## Use High Level Funciton
```
.filter
.map 
之類的

## Use Destructure 簡短你的 Code

## 利用 !! 代表 True
```js
const doesExist = !!object;
```

## Optional Changing & Spread Operator
```js
// Spread operator
const modifiedUser = { ...oldUser, secondPhone: 56459544, Country: "Poland" }
// Optional chaining
const userFirstArticleClaps = user?.articles[0]?.claps.map(() => /*...*/) 
```
-> 思考如果沒有這些 syntax 該怎辦

```

## Use do...while or while to Solve Problem

## 不對 Undefined, Null 做操作
	可利用 optional chaining 去跳過 undefined, null。

## 不要有 Magic Number
	給他變數名稱

## Catch Error
```js
const result1 = await fakeFetch() 
				.catch((error) => { console.log(error.message); });
```

[[functional programming]]
[[SOLID]]
