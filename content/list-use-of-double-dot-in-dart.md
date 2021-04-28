# List的点语法：1点和2点的区别
[List use of double dot (.) in dart?](https://stackoverflow.com/questions/49447736/list-use-of-double-dot-in-dart)

___



> 1

..的情形：当同一个对象，需要重复调用一下方法时：

```
List list = [];
list.add(color1);
list.add(color2);
list.add(color3);
list.add(color4);

// with cascade

List list = [];
list
  ..add(color1)
  ..add(color2)
  ..add(color3)
  ..add(color4);
```

> 2

这是一个瀑布流运算符

```
var l1 = new List<int>()..add(0)..addAll([1, 2, 3]);

运算结果l1会是[0, 1, 2, 3]
```

而如果只有一个点

```
var l1 = new List<int>().add(0).addAll([1, 2, 3]);

会报错，因为.add(0)返回的是void
```





