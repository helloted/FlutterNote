# 如何获取Widget尺寸


> 1

RenderObject：Widget 的渲染由RenderObject 完成，它在Flutter Engine 绘制UI 时处理Widget 的大小、布局和绘制。 每个小部件都有渲染对象，该对象保存在屏幕上绘制的小部件的配置。
没有直接的方法可以计算widget的大小，所以要找到我们必须借助widget的上下文。
调用 context.size 会返回 Size 对象，其中包含小部件的高度和宽度。 context.size 计算小部件的渲染框并返回大小。
调用这个 getter 理论上相对昂贵（树的深度为 O(N)），但实际上通常很便宜，因为树通常有很多渲染对象，因此到最近的渲染对象的距离通常很短。

```
class WidgetSize extends StatefulWidget {
  final Widget child;
  final Function onChange;

  const WidgetSize({
    Key key,
    @required this.onChange,
    @required this.child,
  }) : super(key: key);

  @override
  _WidgetSizeState createState() => _WidgetSizeState();
}

class _WidgetSizeState extends State<WidgetSize> {
  @override
  Widget build(BuildContext context) {
    SchedulerBinding.instance.addPostFrameCallback(postFrameCallback);
    return Container(
      key: widgetKey,
      child: widget.child,
    );
  }

  var widgetKey = GlobalKey();
  var oldSize;

  void postFrameCallback(_) {
    var context = widgetKey.currentContext;
    if (context == null) return;

    var newSize = context.size;
    if (oldSize == newSize) return;

    oldSize = newSize;
    widget.onChange(newSize);
  }
}
```

使用案例

```
Size textSize;
WidgetSize(
  onChange: (Size size) {
    setState(() {
      textSize = size;
    });
  },
  child: Text(
    "Size - $textSize",
    textAlign: TextAlign.center,
  ),
),
```







