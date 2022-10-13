#js 

# Description
> Three types of try statement
- `try...catch`
- `try...finally`
- `try...catch...finally`

# `try...catch`
> the catch-block is executed when any exception is thrown from within the try-block
```js
try {
  throw 'myException'; // generates an exception
} catch (e) {
  // statements to handle any exceptions
  logMyErrors(e); // pass exception object to error handler
}
```

##  Use condition to catch a small subset of expected errors.
```js
try {
  myRoutine();
} catch (e) {
  if (e instanceof RangeError) {
    // statements to handle this very common expected error
  } else {
    throw e;  // re-throw the error unchanged
  }
}
```

## Use `try...catch` to get information 
```js
function isValidJSON(text) {
  try {
    JSON.parse(text);
    return true;
  } catch {
    return false;
  }
}
```

# `finally` 
> Control flow statement(return, throw, break, continue) in the `finally-block` will mask any completion value of the `try-block` or `catch-block`. 

- Before `try-block` returning, the control flow is yielded to the `finally` block first.
```js
function doIt() {
  try {
    return 1;
  } finally {
    return 2;
  }
}

doIt(); // returns 2
```


# Nested `try-blocks` 
> Any given exception will be caught by the nearest `catch-block` unless it is re-thrown.
```js
try {
  try {
    throw new Error('oops');
  } finally {
    console.log('finally');
  }
} catch (ex) {
  console.error('outer', ex.message);
}

// Output:
// "finally"
// "outer" "oops"
```

```js
try {
  try {
    throw new Error('oops');
  } catch (ex) {
    console.error('inner', ex.message);
  } finally {
    console.log('finally');
  }
} catch (ex) {
  console.error('outer', ex.message);
}

// Output:
// "inner" "oops"
// "finally"
```

```js
try {
  try {
    throw new Error('oops');
  } catch (ex) {
    console.error('inner', ex.message);
    throw ex;
  } finally {
    console.log('finally');
  }
} catch (ex) {
  console.error('outer', ex.message);
}

// Output:
// "inner" "oops"
// "finally"
// "outer" "oops"
```

## Returning form `finally-block`
> If the `finally-block` returns a value, this value becomes the return value of the entire `try-catch-finally` statement, regardless of any return statements in the try and catch block.
> 
```js
(() => {
  try {
    try {
      throw new Error('oops');
    } catch (ex) {
      console.error('inner', ex.message);
      throw ex;
    } finally {
      console.log('finally');
      return;
    }
  } catch (ex) {
    console.error('outer', ex.message);
  }
})();

// Output:
// "inner" "oops"
// "finally"
```

[[Error in Js]]
