#cs #js

# Triple Equals
	Triple equals in Js is Strict equality.
	both type and value have to be the same.

# Double Equals
	Double equals in Js is loose equality
	Double equals perform **type coercion**	
- Type coercion: two values are compared after attempting to convert them into the same type.

```js
77 == '77'
// true
```

```js
false == 0
// true
```

# Falsy values
	Type coercion will actually convert our zero to Boolean value false
	There are six falsy values we should be aware of.
-   false
-   0
-   “”
-   null
-   undefined
-   NAN

## Comparasion
1. false, 0, and “”
    - when we compare any of these falsy value with loose equality, they will always be equal. That’s because they will convert into false Boolean.
    
2. null and undefined
    - They are only equal to themselves or each other.
	```js
	null == null
	// true
	
	undefined == undefined
	// true
	
	null == undefined
	// true
	```

3. NaN(not a number)
	NaN is not equivalent to any things, even themselves!!
	```js
	NaN == NaN
	// false
	```
