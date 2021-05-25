# Flutter局部刷新
> 1

当我们调用有状态类的setState方法时会遍历每一个子Widget的State.build刷新状态， 这将是一笔很大的性能开销，所以我们需要使用局部刷新来进行优化。

```
class TestRoute extends StatefulWidget {
  @override
  _TestRouteState createState() => _TestRouteState();
}

class _TestRouteState extends State<TestRoute> {
  int count = 0;

  @override
  Widget build(BuildContext context) {
    return new FlatButton(
      onPressed: () {
        setState(() => count++);
      },
      child: new Text('$count'),
    );
  }
}
```

上面这个案例，会会刷新所有的Wiget

#### 使用GlobalKey局部刷新方式

我们还是用上面的例子，只是通过GlobalKey的方式只刷新局部的Text，

```
class TestRoute extends StatefulWidget {
  @override
  _TestRouteState createState() => _TestRouteState();
}

class _TestRouteState extends State<TestRoute> {
  int count = 0;

  GlobalKey<TextWidgetState> textKey = GlobalKey();

  @override
  Widget build(BuildContext context) {
    return new Column(
      mainAxisAlignment: MainAxisAlignment.center,
      children: <Widget>[
        new TextWidget(textKey), //需要更新的Text
        new FlatButton(
          onPressed: () {
            count++; // 这里我们只给他值变动，状态刷新交给下面的Key事件
            textKey.currentState.onPressed(count);
          },
          child: new Text('按钮 $count'),
        ),
      ],
    );
  }
}

// 封装的文本组件Widget
class TextWidget extends StatefulWidget {
  final Key key;

  // 接收一个Key
  TextWidget(this.key);

  @override
  State<StatefulWidget> createState() => TextWidgetState();
}

class TextWidgetState extends State<TextWidget> {
  String _text = "0";

  @override
  Widget build(BuildContext context) {
    return new Text(_text);
  }

  void onPressed(int count) {
    setState(() => _text = count.toString());
  }
}
```



