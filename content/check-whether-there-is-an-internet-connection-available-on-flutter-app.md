# 判断网络是否可用
[Check whether there is an Internet connection available on Flutter app](https://stackoverflow.com/questions/49648022/check-whether-there-is-an-internet-connection-available-on-flutter-app)

___



> 1

```dart
import 'dart:io';
...
try {
  final result = await InternetAddress.lookup('google.com');
  if (result.isNotEmpty && result[0].rawAddress.isNotEmpty) {
    print('connected');
  }
} on SocketException catch (_) {
  print('not connected');
}
```





