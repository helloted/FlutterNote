# Dart深复制
[How can I clone an Object (deep copy) in Dart?](https://stackoverflow.com/questions/13107906/how-can-i-clone-an-object-deep-copy-in-dart)

___



> 1

Dart里使用from方法来实现： [Clone a List, Map or Set in Dart](https://stackoverflow.com/questions/21744480/clone-a-list-map-or-set-in-dart)

```dart
Map mapA = {
    'foo': 'bar'
};
Map mapB = Map.from(mapA);
```





