#cs #front-end #vue #unit-test 

# introduction
這裡介紹基本用法，之後進階用法再去深入。

## Jest
[官方文件](https://jestjs.io/docs/getting-started)

### [test(name, fn, timeout) 或 it(name, fn, timeout)](https://jestjs.io/docs/api#testname-fn-timeout)
> 一筆測試的最小單位，撰寫測試用 test 去宣告 

test 與 it 是一樣的。

- `name` 測試名稱
- `fn` 要測試的函式
- `timeout` 測試終止前要等待的時間，單位是毫秒

### [expect(value)](https://jestjs.io/docs/expect#expectvalue)
> 每一筆測試都會使用 expect(value) 和 matcher 去匹配某值。

`expect(value)` 的 value 是程式碼產生的值，matcher 帶入的要是正確的值。
下例是 matcher 為 toBe 的範例:
```js
const number = 2

test('test: is 2', () => {
  expect(number).toBe(2)
})
```

### [describe(name, fn)](https://jestjs.io/docs/api#describename-fn)
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

## Vue Test Utils
[官方文件](https://v1.test-utils.vuejs.org/)

### [mount(component, options)](https://next.vue-test-utils.vuejs.org/api/#mount)
> 為寫好的元件掛載，進行操作或斷言。
- options 進行狀態配置，例如傳入 props。

```jsx
import { mount } from '@vue/test-utils'

const Component = {
  template: '<div>Hello world</div>'
}

const ComponentWithProps = {
  template: '<div>{{ msg }}</div>',
  props: {
    msg: {
      type: String,
      required: true
    }
  }
}

describe('Mount example', () => {
  test('mounts a component', () => {
    const wrapper = mount(Component)

    expect(wrapper.html()).toContain('Hello world')
  })

  test('mounts a component with props', () => {
    const wrapper = mount(ComponentWithProps, {
      props: {
        msg: 'Hello world'
      }
    })

    expect(wrapper.html()).toContain('Hello world')
  })
})
```

### [shallowMount()](https://next.vue-test-utils.vuejs.org/api/#shallowmount)
> 與 mount() 相似，差別在於如果 shallowMount 的元件有子元件，不會被 render 出來，會用`<child-stub></child-stub>` 代替。

```jsx
import { mount, shallowMount } from '@vue/test-utils'

const Child = {
  template: "<div>Child component</div>"
}

const Parent = {
  template: "<div><child /></div>",
  components: {
    Child
  }
}

describe('shallowMount example', () => {
  test('test', () => {
    const childShallowWrapper = shallowMount(Child)
    const childMountWrapper = mount(Child)
    console.log(childShallowWrapper.html())
    console.log(childMountWrapper.html())

    const parentShallowWrapper = shallowMount(Parent)
    const parentMountWrapper = mount(Parent)
    console.log(parentShallowWrapper.html())
    console.log(parentMountWrapper.html())
  })
})
```
![[Pasted image 20221012234344.png]]