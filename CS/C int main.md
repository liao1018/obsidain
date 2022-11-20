#cs #c

# Intro
	C 的起手式：int main
```c
#include <stdio.h>
...

int main(void){
	...
}
```

# 如果想傳入參數(arguments)
	main 預設會傳進兩個參數，第一個位置是參數的個數(int)，第一個位置是參數的 string array，string array[0] 為程式的 name。
```c
#include <stdio.h>
#include <cs50.h>

int main(int argc, string argv[]){
	if(argc == 2){
		printf("hello, %s\n", argv[1]);
	}
}
```
`./argv David` → `hello, David`

# 為什麽 output 的 data type 是 int ?
	可以透過 main 的 return 值去判斷該程式的執行情況，是正確或是其他情況之類的，正確的話習慣是 return 0。
```c
{
	if(argc != 2){
		printf("missing argument!");
		return 1;
	}
	printf("hello, %s\n", argv[1]);
	return 0;
}
```
