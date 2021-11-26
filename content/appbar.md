# 设置AppBar的高度？
[Flutter: Setting the height of the AppBar](https://stackoverflow.com/questions/51089994/flutter-setting-the-height-of-the-appbar)

___



> 1

你可以使用[PreferredSize](https://docs.flutter.io/flutter/widgets/PreferredSize-class.html):

```dart
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Example',
      home: Scaffold(
        appBar: PreferredSize(
          preferredSize: Size.fromHeight(50.0), // here the desired height
          child: AppBar(
            // ...
          )
        ),
        body: // ...
      )
    );
  }
}
```





