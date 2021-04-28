# 通过方法或者类来创建一个可重复使用的Widget的区别
[What is the difference between functions and classes to create reusable widgets?](https://stackoverflow.com/questions/53234825/what-is-the-difference-between-functions-and-classes-to-create-reusable-widgets)

___

通过方法

```dart
Widget function({ String title, VoidCallback callback }) {
  return GestureDetector(
    onTap: callback,
    child: // some widget
  );
}
```

通过类

```
class SomeWidget extends StatelessWidget {
  final VoidCallback callback;
  final String title;

  const SomeWidget({Key key, this.callback, this.title}) : super(key: key);

  @override
  Widget build(BuildContext context) {
      return GestureDetector(
        onTap: callback,
        child: // some widget
      );
  }
}
```

区别在哪里呢？用那种更好？

> 1

长话短说，最好用class而不是方法来创建一个可重复使用的Widget-tree.

并不是因为方法会导致问题，而是使用class可以解决问题。

用方法而不是类会有一个最大的区别：The framework is unaware of functions, but can see classes.

举例：

```dart
Widget functionWidget({ Widget child}) {
  return Container(child: child);
}

使用
functionWidget(
  child: functionWidget(),
);
```

如果用类的话

```
class ClassWidget extends StatelessWidget {
  final Widget child;

  const ClassWidget({Key key, this.child}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Container(
      child: child,
    );
  }
}


new ClassWidget(
  child: new ClassWidget(),
);
```

看起来是一样的东西，创建了2个Container，一个嵌套在另外一个里面，但是实际上有轻微区别。

如果，用的是方法创建，生成的widget tree是这样：

```dart
Container
  Container
```

而如果用类来创建，widget tree是这样

```dart
ClassWidget
  Container
    ClassWidget
      Container
```

这很重要，因为更新一个widget时会影响framework的表现。

用方法不一定会导致以下的问题，但是用类肯定可以避免以下问题：

- https://dartpad.dev/1870e726d7e04699bc8f9d78ba71da35
  This example showcases how by splitting your app into functions, you may accidentally break things like `AnimatedSwitcher`
- https://dartpad.dev/a869b21a2ebd2466b876a5997c9cf3f1
  This example showcases how classes allow more granular rebuilds of the widget tree, improving performances
- https://dartpad.dev/06842ae9e4b82fad917acb88da108eee
  This example showcases how, by using functions, you expose yourself to misusing BuildContext and facing bugs when using InheritedWidgets (such as Theme or providers)

结论，二者有一些区别：

Classes:

- 性能优化
- 确保hot-reload正常工作（使用function可能会中断showDialogs及类似功能）
- 确保在两个不同的布局之间切换可以正确处理资源（function可能会重用某些先前的状态）
- 集成到了Widget inspetor里面
  - 可以看到 `ClassWidget` 在widget-tree，可以帮助理解有什么在屏幕上
  - 我们可以重写 [debugFillProperties](https://api.flutter.dev/flutter/foundation/Diagnosticable/debugFillProperties.html) 来打印Widget传的参数
- 错误信息表现更多
- 可以定义 keys
- 可以用 context API

Functions:

- 更少的代码

