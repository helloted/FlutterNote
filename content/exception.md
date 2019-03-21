# Flutter话题的一些整理
1. 

```
flutter: The following assertion was thrown during performResize():
flutter: Vertical viewport was given unbounded height.
```

因为 Column 作为 Flex 它不知道应该如何安放一个 **as big as possible** 的 widget。解决方法也很简单，只要设置 ListView 的 shrinkWrap: true`即可。这就是告诉 ListView 把自己尽可能地缩小。

2、

```
type 'String' is not a subtype of type 'int'
```

这是给int类型的变量赋值了string类型