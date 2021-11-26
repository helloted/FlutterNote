# var vs dynamic
[Difference between "var" and "dynamic" type in Dart?](https://stackoverflow.com/questions/12416507/difference-between-var-and-dynamic-type-in-dart)

___



> 1

`dynamic` 是所有 Dart 对象的基础类型。 在大多数情况下，您不需要明确使用它。

`var` 是一个关键字，意思是“我不关心这里的类型是什么。” Dart 将用初始化类型替换 `var` 关键字，如果没有初始化，则默认保留为 `dynamic`。

如果您希望变量赋值在其生命周期内发生变化，请使用 `var`：

```dart
var msg = "Hello world.";
msg = "Hello world again.";
```

如果您希望变量赋值在其生命周期内保持不变，请使用 `final`： 

```dart
final msg = "Hello world.";
```

使用“final”（自由地）将帮助您发现您无意中意外更改了变量分配的情况。

请注意，当涉及到对象时，`final` 和 `const` 之间有很好的区别。 `final` 不一定使对象本身不可变，而 `const` 可以：

```dart
// can add/remove from this list, but cannot assign a new list to fruit.
final fruit = ["apple", "pear", "orange"];
fruit.add("grape");

// cannot mutate the list or assign a new list to cars.
final cars = const ["Honda", "Toyota", "Ford"];

// const requires a constant assignment, whereas final will accept both:
const names = const ["John", "Jane", "Jack"];
```





