#cs #engineer 

# Code 的重點
1.  Correctness
2.  Well-designed
3.  Well-styled

# 原則
> Clean code → Readable code
## 減少互相耦合的機會

## Better naming
- Variable name should tell their types.
- 
## Don’t Repeat Yourself!(DRY)

## Single responsibility principle
- One purpose functions compose one multiple purposes function.
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

## Recursion can be more concise
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

## Use guard clauses to avoid deep nesting
```js
const getUSTime = (time) => {

if(time <= 12) return time + "AM"

return time + "PM"

}
```

## Use destructure to spare your code

## Optional changing & spread operator
```js
// Spread operator
const modifiedUser = { ...oldUser, secondPhone: 56459544, Country: "Poland" }
// Optional chaining
const userFirstArticleClaps = user?.articles[0]?.claps.map(() => /*...*/) 
```
-> 思考如果沒有這些 syntax 該怎辦

## Use high level funciton

## Use do...while or while to solve problem

## 不對 undefined, null 做操作
	可利用 optional chaining 去跳過 undefined, null。

## 註解提供目的



[[functional programming]]
