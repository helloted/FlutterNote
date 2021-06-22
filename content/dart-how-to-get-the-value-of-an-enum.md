# 获取枚举Enum的值？
[Dart How to get the “value” of an enum](https://stackoverflow.com/questions/29567236/dart-how-to-get-the-value-of-an-enum)

___

```dart
enum day {MONDAY, TUESDAY}
print( 'Today is $day.MONDAY');
print( 'Today is $day.MONDAY.toString()');
如何获取枚举的字符串
```

> 1

可以通过下面的方法来获取到字符串

```dart
day theDay = day.MONDAY;      
print(theDay.toString().substring(theDay.toString().indexOf('.') + 1));
```

推荐用上面这个，下面这个方法虽然短一些，但是效率低一些

```dart
theDay.toString().split('.').last
```

如果你想遍历所有的值，可以使用 `day.values`:

```dart
for (day theDay in day.values) {
  print(theDay);
}
```





