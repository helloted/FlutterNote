# Widget里的child属性如何使用条件语句？
[How to use conditional statement within child attribute of a Flutter Widget (Center Widget)](https://stackoverflow.com/questions/49713189/how-to-use-conditional-statement-within-child-attribute-of-a-flutter-widget-cen)

___



> 1

使用Builder Widget，可以创建一个闭包函数

```dart
Container(
      child: Builder(
          builder: (context) {
            // any logic needed...
            return Container();
          }
      ),
    )
```

使用三元运算符

```dart
Container(
      child: condition ? Text("True") : null,
    );
```

用一个函数，在函数里面使用条件语句

```dart
child: getWidget()

Widget getWidget() {
  if (x > 5) ...
  //more logic here and return a Widget
```







