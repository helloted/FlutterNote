# 如何在Widget build完毕后调用方法
[Flutter: Run method on Widget build complete](https://stackoverflow.com/questions/49466556/flutter-run-method-on-widget-build-complete)

___

> 1

```dart
  void initState() {
    super.initState();
    WidgetsBinding.instance
        .addPostFrameCallback((_) => yourFunction(context));
  }
```

> 2

有两个方式

```dart
WidgetsBinding.instance
        .addPostFrameCallback((_) => yourFunction(context));
```

或者

```dart
import 'package:flutter/scheduler.dart';

SchedulerBinding.instance.addPostFrameCallback((_) => yourFunction(context));
```

