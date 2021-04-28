# 合并list
[How do I combine two lists in Dart?](https://stackoverflow.com/questions/21826342/how-do-i-combine-two-lists-in-dart)

___



> 1

You can use:

```dart
var newList = new List.from(list1)..addAll(list2);
```

If you have several lists you can use:

```dart
var newList = [list1, list2, list3].expand((x) => x).toList()
```

As of Dart 2 you can now use `+`:

```dart
var newList = list1 + list2 + list3;
```

As of Dart 2.3 you can use the spread operator:

```dart
var newList = [...list1, ...list2, ...list3];
```





