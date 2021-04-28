# Dart程序中如何sleep
[How can I “sleep” a Dart program](https://stackoverflow.com/questions/18449846/how-can-i-sleep-a-dart-program)

___



> 1

```dart
import 'dart:async';

Future sleep1() {
  return new Future.delayed(const Duration(seconds: 1), () => "1");
}

Future sleep2() {
  return new Future.delayed(const Duration(seconds: 2), () => "2");
}
```

> 2

### In Async Code

```dart
await Future.delayed(Duration(seconds: 1));
```

### In Sync Code

```dart
import 'dart:io';

sleep(Duration(seconds:1));
```

