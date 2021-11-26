# 怎么判断应用是否在前台？
[How do I check if the Flutter application is in the foreground or not?](https://stackoverflow.com/questions/51835039/how-do-i-check-if-the-flutter-application-is-in-the-foreground-or-not)

___



> 1

在State<...> 声明 [WidgetsBindingObserver](https://docs.flutter.io/flutter/widgets/WidgetsBindingObserver-class.html) 然后监听接口. 类似这样

```dart
class _MyHomePageState extends State<MyHomePage> with WidgetsBindingObserver {
  AppLifecycleState _notification; 
  @override
  void didChangeAppLifecycleState(AppLifecycleState state) {
    setState(() {
      _notification = state;
    });
  }

  @override
  initState() {
    super.initState();
    WidgetsBinding.instance.addObserver(this);
    ...
  }

  @override
  void dispose() {
    WidgetsBinding.instance.removeObserver(this);
    super.dispose();
  }
}
```





