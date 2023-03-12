[說明文章](https://ithelp.ithome.com.tw/articles/10266005)
# introduction
在 Vue 當中，我們會利用 scoped 避免父元件的 style 影響到子元件內部元素，避免污染。但有時我們會需要某些 style 可以套用到子元件。這時候就需要用到樣式穿透，讓父元素設定的 style 可以傳到子元件。

用法如下：

```css
# SCSS 無法使用
.home >>> .message {
    color: red;
}
```

```css
.home:deep .message {
    color: red;
}
```

```css
.home /deep/ .message {
    color: red;
}
```

```css
.home::v-deep .message {
    color: red;
}
```

# 補充
Vue 會預設儘管是設置 scope，也會影響到子元件的根元素，這樣可以方便父元件做佈局