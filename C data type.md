#c 

[各 data type 所佔空間](https://www.tutorialspoint.com/cprogramming/c_data_types.htm)

# Introduction
> 宣告會利用 data type，而確立 data type 就確立該變數所佔的 storage。

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

# 補充
> values of type char must be wrapped in single quotes.
```c
char c = 'Y';
```