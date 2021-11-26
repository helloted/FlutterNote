# Column可滚动
[Flutter - How to make a column screen scrollable](https://stackoverflow.com/questions/52053850/flutter-how-to-make-a-column-screen-scrollable)

___



> 1

The `ListView` 可以实现类似功能或者使用 `SingleChildScrollView`:

```dart
return new Container(
  child: new SingleChildScrollView(
    child: new Column(
      children: <Widget>[
        _showChild1(),
        _showChild2(),
        ...
        _showChildN()
      ]
    )
  )
);
```





