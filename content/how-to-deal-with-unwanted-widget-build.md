# 如何处理Widget的非必要bulid调用
[How to deal with unwanted widget build?](https://stackoverflow.com/questions/52249578/how-to-deal-with-unwanted-widget-build)

___

```
@override
Widget build(BuildContext context) {
  return FutureBuilder(
    future: httpCall(),
    builder: (context, snapshot) {
      // create some layout here
    },
  );
}
```

在这个案例里，如果build方法被重新调用，会触发http，这个不是我期望的。

> 1

bulid方法设计的时候是被认为应该是纯净/没有其他效应的，这是因为下列额外的因素会引发widget的bulid调用，比如：

- Route pop/Push
- 屏幕尺寸调整，一般是因为键盘或者屏幕方向改变导致
- 父Widget重新创建child
- 继承的Wiget依赖`Class.of(context)` pattern改变了

这意味着，在build方法里不要触发一个http调用或者修改任何的state。

<!------------------------------------->

在这个案例里，你应该让你的build方法变得纯净，而不是去阻止build的调用，从而build方法可以任意时间调用。

你应该把你的Widget转换成一个StatefulWidget，然后将HTTP调用释放出来，放到State的initState里面

```
class Example extends StatefulWidget {
  @override
  _ExampleState createState() => _ExampleState();
}

class _ExampleState extends State<Example> {
  Future<int> future;

  @override
  void initState() {
    future = Future.value(42);
    super.initState();
  }

  @override
  Widget build(BuildContext context) {
    return FutureBuilder(
      future: future,
      builder: (context, snapshot) {
        // create some layout here
      },
    );
  }
}
```

如果你一定要优化rebulids，你可以创建一个Wiget，在rebuilding的时候，它的child不会被强制build。

最简单的方式就是利用关键字const

```
@override
Widget build(BuildContext context) {
  return const DecoratedBox(
    decoration: BoxDecoration(),
    child: Text("Hello World"),
  );
}
```

多亏了const关键字，DecoratedBox对象会保持不变即使build方法被调用了无数次。

还有一个方法就是利用finnal关键字

```
@override
Widget build(BuildContext context) {
  final subtree = MyWidget(
    child: Text("Hello World")
  );

  return StreamBuilder<String>(
    stream: stream,
    initialData: "Foo",
    builder: (context, snapshot) {
      return Column(
        children: <Widget>[
          Text(snapshot.data),
          subtree,
        ],
      );
    },
  );
}
```

上面的代码中，不管是StreamBuilder有新的值还是Column rebuild，subtree这个对象都能保持不变。

> 2

你可以用下面的步骤来阻止不必要的build调用

1. 给一块独立的UI创建一个子Stateful的类
2. 使用Provier库，这样你可以阻止不必要的bulid调用

下面情况会引发build调用

- [initState](https://api.flutter.dev/flutter/widgets/State/initState.html)调用之后
-  [didUpdateWidget](https://api.flutter.dev/flutter/widgets/State/didUpdateWidget.html)调用之后
-  [setState()](https://api.flutter.dev/flutter/widgets/State/setState.html) 被调用
- 键盘打开
- 屏幕方向改变
- 父widget build了导致child widget同样被rebuild

> 3

Flutter 有 `ValueListenableBuilder<T> class `.这个类允许你在必要的时候才去rebuild widget。

```
return Scaffold(
  appBar: AppBar(
    title: Text(widget.title)
  ),
  body: Center(
    child: Column(
      mainAxisAlignment: MainAxisAlignment.center,
      children: <Widget>[
        Text('You have pushed the button this many times:'),
        ValueListenableBuilder(
          builder: (BuildContext context, int value, Widget child) {
            // This builder will only get called when the _counter
            // is updated.
            return Row(
              mainAxisAlignment: MainAxisAlignment.spaceEvenly,
              children: <Widget>[
                Text('$value'),
                child,
              ],
            );
          },
          valueListenable: _counter,
          // The child parameter is most helpful if the child is
          // expensive to build and does not depend on the value from
          // the notifier.
          child: goodJob,
        )
      ],
    ),
  ),
  floatingActionButton: FloatingActionButton(
    child: Icon(Icons.plus_one),
    onPressed: () => _counter.value += 1,
  ),
);
```

