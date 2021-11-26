# 判断软键盘是否开启？
[Flutter: Detect keyboard open/close](https://stackoverflow.com/questions/48750361/flutter-detect-keyboard-open-close)

___



> 1

在Widget树中用来检测： `viewInsets.bottom` 是否等于0判断键盘是否开启

```dart
MediaQuery.of(context).viewInsets.bottom
```



