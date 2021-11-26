# 如何在Build方法里调用async?
[How do I call async property in Widget build method](https://stackoverflow.com/questions/53800662/how-do-i-call-async-property-in-widget-build-method)

___



> 1

建议使用FutureBuilder

```dart
import 'package:flutter/material.dart';

class MyApp extends StatefulWidget {
  @override
  _MyAppState createState() => _MyAppState();
}

class _MyAppState extends State<MyApp> {
  // save in the state for caching!
  DeviceInfoPlugin _deviceInfoPlugin;

  @override
  void initState() {
    super.initState();
    _deviceInfoPlugin = DeviceInfoPlugin();
  }

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'My Device Info',
      home: Scaffold(
        appBar: AppBar(
          title: Text('My Device Info'),
        ),
        body: FutureBuilder<AndroidDeviceInfo>(
          future: _deviceInfoPlugin.androidInfo,
          builder: (BuildContext context, AsyncSnapshot<AndroidDeviceInfo> snapshot) {
            if (!snapshot.hasData) {
              // while data is loading:
              return Center(
                child: CircularProgressIndicator(),
              );
            } else {
              // data loaded:
              final androidDeviceInfo = snapshot.data;
              return Center(
                child: Text('Android version: ${androidDeviceInfo.version}'),
              );
            }
          },
        ),
      ),
    );
  }
}
```





