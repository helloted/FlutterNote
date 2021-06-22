# 合并list
[How do I combine two lists in Dart?](https://stackoverflow.com/questions/21826342/how-do-i-combine-two-lists-in-dart)

___



> 1

可以

```dart
var newList = new List.from(list1)..addAll(list2);
```

或者

```dart
var newList = [list1, list2, list3].expand((x) => x).toList()
```

Dar2之后可以用 `+`:

```dart
var newList = list1 + list2 + list3;
```

 Dart 2.3 之后可以这样用:

```dart
var newList = [...list1, ...list2, ...list3];
```

