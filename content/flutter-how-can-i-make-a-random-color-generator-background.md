# 随机的背景颜色
[Flutter: How can I make a Random color generator Background](https://stackoverflow.com/questions/51340588/flutter-how-can-i-make-a-random-color-generator-background)

___



> 1

```dart
Color((math.Random().nextDouble() * 0xFFFFFF).toInt()).withOpacity(1.0)
```





