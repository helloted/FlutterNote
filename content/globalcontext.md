# 获取全局Context？
___



> 1

```
static final navKey = new GlobalKey<NavigatorState>();
```

```dart
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      // ...
      navigatorKey: NavKey.navKey,
      // ...
    );
  }
}
```

使用

```dart
navigatorKey.currentContext
```



