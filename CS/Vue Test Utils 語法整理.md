#cs #front-end #vue #unit-test 

[官方文件](https://v1.test-utils.vuejs.org/)

# API
## [mount(component, options)](https://next.vue-test-utils.vuejs.org/api/#mount)
> 為寫好的元件掛載，進行操作或斷言。並產生 wrapper 物件，可以執行各種 Wrapper 的 API 操作。
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

    expect(wrapper.html()).toMatch('Hello world')
  })

  test('mounts a component with props', () => {
    const wrapper = mount(ComponentWithProps, {
      props: {
        msg: 'Hello world'
      }
    })

    expect(wrapper.html()).toMatch('Hello world')
  })
})
```

## [shallowMount()](https://next.vue-test-utils.vuejs.org/api/#shallowmount)
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


# Wrapper
## [find('dom')](https://v1.test-utils.vuejs.org/zh/api/wrapper/#find)
> 返回第一個 DOM 節點，也是一個 Wrapper，就算是 nested 也可以。是使用了`querySelector` 语法)

```js
import { shallowMount } from '@vue/test-utils';
import HelloWorld from '@/components/HelloWorld.vue';
  
describe('HelloWorld.vue', () => {
	it('check if hello class exists', () => {
		const msg = 'new message';
		const wrapper = shallowMount(HelloWorld, {
			props: { msg },
		});
	  
		const helloWrapper = wrapper.find('h1');
		expect(helloWrapper.exists()).toBe(true);
	});
});
```
### 善用 dataset 去 query
> data-set 功能就是用來知道說這個選擇器就會對應一組 Test
```js
import { mount } from '@vue/test-utils';

const Component = {
  template: '<div data-test="target">dataset</div>'
}

test('render dataset', () => {
  const wrapper = mount(Component);

  expect(wrapper.get('[data-test="target"]').exist()).toBe(true);
});
```

## [exist()](https://v1.test-utils.vuejs.org/zh/api/wrapper/#exists)
> 	判斷 Wrapper 是否存在。

## [html](https://v1.test-utils.vuejs.org/zh/api/wrapper/#html)
> 返回該 Wrapper 的 html。

```js
import { mount } from '@vue/test-utils'
import Foo from './Foo.vue'

const wrapper = mount(Foo)
expect(wrapper.html()).toBe('<div><p>Foo</p></div>')
```

## [text](https://v1.test-utils.vuejs.org/zh/api/wrapper/#text)
> 返回 Wrapper 的全部文本內容。會把它結合成一個字串。

```js
import { mount } from '@vue/test-utils'
import Foo from './Foo.vue'

const wrapper = mount(Foo)
expect(wrapper.text()).toBe('bar')
```

## [trigger](https://v1.test-utils.vuejs.org/zh/api/wrapper/#trigger)
> 在該 wrapper 異步觸發事件，會返回一個 promise，當 promise 被解決，確保 wrapper 已被更新。

```js
test('after click, count will be 1', async () => {
  const wrapper = mount(Component)

  await wrapper.get('[data-test="button"]').trigger('click')

  expect(wrapper.get('[data-test="count"]').text()).toBe('1')
})
```

## [emmited](https://v1.test-utils.vuejs.org/zh/api/wrapper/#emitted)
> 返回一個 wrapper vm 發出的自定義事件的對象的物件。

```js
import { mount } from '@vue/test-utils'

test('emit demo', async () => {
  const wrapper = mount(Component)

  wrapper.vm.$emit('foo')
  wrapper.vm.$emit('foo', 123)

  await wrapper.vm.$nextTick() // 等待事件处理完成

  /*
  wrapper.emitted() 返回如下对象：
  {
    foo: [[], [123]]
  }
  */


	// 断言事件已经被触发
	expect(wrapper.emitted('foo')).toBeTruthy()
	
	// 断言事件的数量
	expect(wrapper.emitted('foo').length).toBe(2)
	
	// 断言事件的有效数据
	expect(wrapper.emitted('foo')[1]).toEqual([123])
```