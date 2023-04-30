#cs #js

# Intro
-   Primitive type
-   Object type

# Primitive type
-   String
-   Number
-   Boolean
-   Null
-   Undefined

## typeof
	除了 null 以外，都可以用 `typeof` 去判斷。如果是 null，要用 === null 去判斷。
	- typeof null 會是 object。

## Object wrapper 
	除了 null, undefined 以外，其他 primitive type 都會用 object wrapper 包在外面，使其有一些 methods 得以使用。

## null vs undefined
	概念上說，undefined 是 absense of value，null 是 absense of object。

## undefined
	一個 function return no value 接收到的值，是 undefined。

# Object type
	一般來說是以下幾類
-   Object
-   Function
-   Array
-   Set

# 補充
[[JS Object]]
[[Js Map & Object 差別]]