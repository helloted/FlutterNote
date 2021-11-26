# 如何在弹窗消失时候执行代码？
[How to run code after showDialog is dismissed in Flutter?](https://stackoverflow.com/questions/49706046/how-to-run-code-after-showdialog-is-dismissed-in-flutter)

___



> 1

 `then` block会在弹窗消失之后执行

```dart
showDialog(
  // Your Dialog Code
).then((val){
  Navigator.pop(_context);
});
```





