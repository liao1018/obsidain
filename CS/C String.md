#cs #c

# Intro
	如果要去儲存一個 String，因為是連續記憶體，需要讓電腦知道 String 結束的地方，所以我們需要浪費一個 Byte 在 String 的結尾，用 ASCII NUL 來表示，轉換成數字就是 0。
![[Pasted image 20221120145959.png]]
![[Pasted image 20221120151002.png]]

## 利用程式 print 看看
	先利用 cs50 的 library 去使用 string type。
```c
#include <cs50.h>
#include <stdio.h>

int main(void){
	string s = "Hi!";
	
	printf("%i %i %i %i\n", s[0], s[1], s[2], s[3]);
}
```
→ `72 73 33 0` (ASCII)

# <string.h>
	裡面有一些 string 用的 methods，例如 strlen(s)，會 output int 為 string 的 length。

# 例子：to upper case
```c
for(int i = 0, n = strlen(s); i < n; i++){
	if(s[i] >= 'a' && s[i] <= 'z'){
		printf("%c", s[i] - 32);
	}
	else
	{
		printf("%c", s[i]);
	}
}
```

## <ctype.h> 變成更好的設計
```c
#include <ctype.h>

...

for(int i = 0, n = strlen(s); i < n; i++){
	printf("%c", toupper(s[i]));
}
```


