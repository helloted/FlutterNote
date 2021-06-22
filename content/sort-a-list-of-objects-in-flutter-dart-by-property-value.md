# 根据某个属性对list排序
[Sort a list of objects in Flutter (Dart) by property value](https://stackoverflow.com/questions/53547997/sort-a-list-of-objects-in-flutter-dart-by-property-value)

___



> 1

可以用List.sort方法

```dart
someLists.sort((a, b) => a.someProperty.compareTo(b.someProperty));
```

> 2

如果你想要用name属性来进行排序：

```dart
objects.sort((a, b) {
  return a.value['name'].toString().toLowerCase().compareTo(b.value['name'].toString().toLowerCase());
});    
```

