# 显示/隐藏一个Widge
[Show/hide widgets in Flutter programmatically](https://stackoverflow.com/questions/44489804/show-hide-widgets-in-flutter-programmatically)

___



> 1

不可见：Widgt实际上在屏幕上有，但是对于用户不可见

```dart
Visibility(
  child: Text("Invisible"),
  maintainSize: true, 
  maintainAnimation: true,
  maintainState: true,
  visible: false, 
),
```

消失：整个widget没有占用任何物理空间

```dart
Visibility(
  child: Text("Gone"),
  visible: false,
),
```

或者，也可以用if来

```dart
Column(
  children: <Widget>[
    if (show) Text("This can be visible/not depending on condition"),
    Text("This is always visible"),
  ],
) 
```



