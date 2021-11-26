# Navigation Pop到第一页面
[Flutter Navigation pop to index 1](https://stackoverflow.com/questions/49672706/flutter-navigation-pop-to-index-1)

___



> 1

如果没有使用名字导航，可以使用如下:

```dart
Navigator.of(context).popUntil((route) => route.isFirst);
```
