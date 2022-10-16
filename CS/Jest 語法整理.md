#cs #front-end #unit-test

[官方文件](https://jestjs.io/docs/getting-started)

# Global
## [test(name, fn, timeout) 或 it(name, fn, timeout)](https://jestjs.io/docs/api#testname-fn-timeout)
> 一筆測試的最小單位，撰寫測試用 test 去宣告 

test 與 it 是一樣的。

- `name` 測試名稱
- `fn` 要測試的函式
- `timeout` 測試終止前要等待的時間，單位是毫秒

## [describe(name, fn)](https://jestjs.io/docs/api#describename-fn)
> describe 用來講多個測試整合，可以有個命名。

```jsx
const number = 2

describe('Number', () => {
  test('is 2', () => {
    expect(number).toBe(2)
  })

  test('is even', () => {
    expect(number % 2).toBe(0)
  })
})
```

# expect
## [expect(value)](https://jestjs.io/docs/expect#expectvalue)
> 每一筆測試都會使用 expect(value) 和 matcher 去匹配某值。

`expect(value)` 的 value 是程式碼產生的值，matcher 帶入的要是正確的值。
下例是 matcher 為 toBe 的範例:
```js
const number = 2

test('test: is 2', () => {
  expect(number).toBe(2)
})
```

## [toBe(value)](https://jestjs.io/docs/next/expect#tobevalue)
> to compare primitive values or check referential identity of object instances. 實際上是用了 `Object.is()` 去判斷是否一樣。

```js
const can = {
  name: 'pamplemousse',
  ounces: 12,
};

describe('the can', () => {
  test('has 12 ounces', () => {
    expect(can.ounces).toBe(12);
  });

  test('has a sophisticated name', () => {
    expect(can.name).toBe('pamplemousse');
  });
});
```

## [toMatch(regexp | string)](https://jestjs.io/docs/expect#tomatchregexp--string)
> 會去對應字串有沒有該 string，也可以輸入正規表達式。
```js
describe('grapefruits are healthy', () => {
  test('grapefruits are a fruit', () => {
    expect('grapefruits').toMatch('fruit');
  });
});
```