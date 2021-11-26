# 怎么删除List重复值?
[How can I delete duplicates in a Dart List? list.distinct()?](https://stackoverflow.com/questions/12030613/how-can-i-delete-duplicates-in-a-dart-list-list-distinct)

___



> 1

使用toSet

```dart
  var ids = [1, 4, 4, 4, 5, 6, 6];
  var distinctIds = ids.toSet().toList();
```

结果: [1, 4, 5, 6]

**Or with spread operators:**

```dart
var distinctIds = [...{...ids}];
```





