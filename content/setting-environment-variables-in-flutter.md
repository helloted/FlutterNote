# 设置环境变量
[Setting environment variables in Flutter](https://stackoverflow.com/questions/44250184/setting-environment-variables-in-flutter)

___



> 1

从 Flutter 1.17 开始，您可以根据需要定义编译时变量。 

为此，只需在 `flutter run` 或 `flutter build` 期间使用 `--dart-define` 参数 如果需要传递多个键值对，只需多次定义`--dart-define`： 

```sh
flutter run --dart-define=SOME_VAR=SOME_VALUE --dart-define=OTHER_VAR=OTHER_VALUE
```

在代码中使用:

```dart
const SOME_VAR = String.fromEnvironment('SOME_VAR', defaultValue: 'SOME_DEFAULT_VALUE');
const OTHER_VAR = String.fromEnvironment('OTHER_VAR', defaultValue: 'OTHER_DEFAULT_VALUE');
```







