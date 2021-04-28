# Expanded VS Flexible
[Flutter: Expanded vs Flexible](https://stackoverflow.com/questions/52645944/flutter-expanded-vs-flexible)

___



> 1

Flexible只会取需要的空间，Expanded会取所有可用的空间

```dart
Scaffold(
  appBar: AppBar(),
  body: Column(
    children: <Widget>[
      Row(
        children: <Widget>[
          buildExpanded(),
          buildFlexible(),
        ],
      ),
      Row(
        children: <Widget>[
          buildExpanded(),
          buildExpanded(),
        ],
      ),
      Row(
        children: <Widget>[
          buildFlexible(),
          buildFlexible(),
        ],
      ),
    ],
  ),
);
```

![img](./../images/10.png)



