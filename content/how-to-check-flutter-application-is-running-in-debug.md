# 如何判断当前是否是Release模式？
[How to check flutter application is running in debug?](https://stackoverflow.com/questions/49707028/how-to-check-flutter-application-is-running-in-debug)

___



> 1

使用kReleaseMode来判断

```dart
import 'package:flutter/foundation.dart';
```

```dart
if(kReleaseMode){ // is Release Mode ??
    print('release mode');
} else {
    print('debug mode');
}
```





