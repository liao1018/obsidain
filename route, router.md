標籤： #vue 

---
### vue3 用法
```javascript
import { useRouter, useRoute } from "vue-router";

//...

setup() {
  const router = useRouter();
  const route = useRoute();

  const onSubmit = () => {
    router.push({ name: "Home" });
  }
  const showParams = () => {
    console.log(route.params);
  }
}
```

### route 
- route 優先度：前面寫>後面寫，所以可以啥網址都會導向的網頁寫在最後

### router
- 可以利用process.env.BASE_URL，去偵測環境的根目錄，如果不是deploy 在根目錄上時，可以配合使用，參考[[vue.config.js]]
```js
const router = createRouter({

history: createWebHistory(process.env.BASE_URL),

routes,

});
```

---

[[push, replace 差異]]