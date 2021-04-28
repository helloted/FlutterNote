# Dart拓展Extension
[How do I use Dart extension functions?](https://stackoverflow.com/questions/58288235/how-do-i-use-dart-extension-functions)

___



> 1

#### 静态拓展变量

这里有一个案例：

```dart
extension FancyNum on num {
  num plus(num other) => this + other;

  num times(num other) => this * other;
}
```

可以使用这样：

```dart
print(5.plus(3)); // Equal to "5 + 3".
print(5.times(8)); // Equal to "5 * 8".
print(2.plus(1).times(3)); // Equal to "(2 + 1) * 3".
```

需要注意的是，名称 `FancyNum` 是可选的，下列格式也是可以的

```dart
extension on num {}
```

但你如果要在其他文件使用，你需要给一个名字

下面也可以：

```dart
print(FancyNum(1).plus(2));
```





