# 给一个StatefulWidget传值并在state里获取
[Passing data to StatefulWidget and accessing it in it's state in Flutter](https://stackoverflow.com/questions/50287995/passing-data-to-statefulwidget-and-accessing-it-in-its-state-in-flutter)

___

有两页屏，一个是记录展示，一个是记录编辑。需要传一个对象到第二个页面

```dart
class RecordPage extends StatefulWidget {
  final Record recordObject;

  RecordPage({Key key, @required this.recordObject}) : super(key: key);

  @override
  _RecordPageState createState() => new _RecordPageState();
}

class _RecordPageState extends State<RecordPage> {
  @override
  Widget build(BuildContext context) {
   //.....
  }
}
```

怎么样在RecordPageState获取recordObject?

> 1

可以类似这样的写法widget.objectname

```dart
class _RecordPageState extends State<RecordPage> {
  @override
  Widget build(BuildContext context) {
   .....
   widget.recordObject
   .....
  }
}
```







