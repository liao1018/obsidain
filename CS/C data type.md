#cs #c

[各 data type 所佔空間](https://www.tutorialspoint.com/cprogramming/c_data_types.htm)

# Introduction
> 宣告會利用 data type，而確立 data type 就確立該變數所佔的 storage。

# Numbers of bytes
| type   | number of bytes | note                                                            |
| ------ | --------------- | --------------------------------------------------------------- |
| bool   | 1 bytes         | min unit in a computer is 1 byte, even if we only need one bit. |
| char   | 1 bytes         | ASCII                                                           |
| float  | 4 bytes         |                                                                 |
| double | 8 bytes         |                                                                 |
| int    | 4 bytes         |                                                                 |
| long   | 8 bytes         |                                                                 |

## 補充：We use the store of RAM.
## 補充：char 
	values of type char must be wrapped in single quotes.
```c
char c = 'Y';
```

# 變換 data type 的計算
```c
#include <stdio.h>

int main(void){
	int x = 1;
	int y = 2;
	
	float z = (float) x / (float) y;
	printf("%f\n", z);
}
```

# 補充: const 
	Constants must be all capital in convention.
```c
const int TOTAL = 3;
```

# Memory 僅是儲存 Bytes
	我們可以轉換 Type 去看背後儲存了什麼。
```c
#include <stdio.h>

int main(void){
	char c = '#';

	printf("%i", c);
}
```
→ `35`

## Why 35 ??
	因為事實上 char 會透過 ASCII 儲存，而 # 在 ASCII 裡就是用 35 去儲存。
![[Pasted image 20221120145959.png]]

[[C Array]]