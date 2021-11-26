# 如何根据父Widget尺寸来动态调整？
[How can I layout widgets based on the size of the parent?](https://stackoverflow.com/questions/41558368/how-can-i-layout-widgets-based-on-the-size-of-the-parent)

___



> 1

可以使用LayoutBuilder

 `LayoutBuilder`使用 `build()` 方法 有一个标准的 [BuildContext](https://docs.flutter.io/flutter/widgets/BuildContext-class.html) 附带参数 [BoxConstraints](https://docs.flutter.io/flutter/rendering/BoxConstraints-class.html) 帮助动态渲染尺寸.

```dart
var container = Container(
  // Toggling width from 100 to 300 will change what is rendered
  // in the child container
  width: 100.0,
  // width: 300.0
  child: LayoutBuilder(
    builder: (BuildContext context, BoxConstraints constraints) {
      if(constraints.maxWidth > 200.0) {
        return Text('BIG');
      } else {
        return Text('SMALL');
      }
    }
  ),
);
```



