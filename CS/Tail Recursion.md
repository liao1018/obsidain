#cs #clean-code

	在程式的最後 return 並 call 自己，可以減少 stack 溢出佔用記憶體空間。
```js
function factorial(n, result = 1) {
  if (n === 0) {
    return result;
  }
  return factorial(n - 1, n * result);
}

factorial(5); // 120
```