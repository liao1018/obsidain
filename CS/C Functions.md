#cs #c

# Define a Function
> The general form of function definition in C is as follows
> 
```c
return_type function_name( parameter list ) {
   body of the function
}
```

## If no input, put void into params
```c
return_type function_name(void) {
   body of the function
}
```

## Example 
```c
/* function returning the max between two numbers */
int max(int num1, int num2) {

   /* local variable declaration */
   int result;
 
   if (num1 > num2)
      result = num1;
   else
      result = num2;
 
   return result; 
}
```

# Function Declarations
> A function declaration tells the compiler how to call the function. The actual body of function can be defined seperately.

```c
return_type function_name( parameter list );
```
## Example
```c
int max(int num1, int num2);
int max(int, int);
```
Parameter names are not important in function declaration.

# The whole example
```c
#include <stdio.h>
 
/* function declaration */
int max(int num1, int num2);
 
int main () {

   /* local variable definition */
   int a = 100;
   int b = 200;
   int ret;
 
   /* calling a function to get max value */
   ret = max(a, b);
 
   printf( "Max value is : %d\n", ret );
 
   return 0;
}
 
/* function returning the max between two numbers */
int max(int num1, int num2) {

   /* local variable declaration */
   int result;
 
   if (num1 > num2)
      result = num1;
   else
      result = num2;
 
   return result; 
}

```

[[Function call by value or reference in C]]
