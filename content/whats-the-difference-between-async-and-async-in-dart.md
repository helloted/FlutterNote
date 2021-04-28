# async和async*的区别？
[What's the difference between async and async* in Dart?](https://stackoverflow.com/questions/55397023/whats-the-difference-between-async-and-async-in-dart)

___



> 1

简短回答

- `async` 给你一个 `Future`
- `async*` 给你一个 `Stream`.

#### async

当某个方法需要耗时很长时，你给这个方法添加一个async的关键字，会返回一个Future包裹的结果。

```dart
Future<int> doSomeLongTask() async {
  await Future.delayed(const Duration(seconds: 1));
  return 42;
}
```

可以这样使用await来获取结果

```dart
main() async {
  int result = await doSomeLongTask();
  print(result); // prints '42' after waiting 1 second
}
```

#### async*

在一个函数前添加async*的关键字，可以不断返回Future值，结果包裹在Stream里

```dart
Stream<int> countForOneMinute() async* {
  for (int i = 1; i <= 60; i++) {
    await Future.delayed(const Duration(seconds: 1));
    yield i;
  }
}
```

使用 `yield` 来返回一个值，而不是用`return` 因为并没有离开方法

你可以使用 `await for` 来等待Stream的每个值.

```dart
main() async {
  await for (int i in countForOneMinute()) {
    print(i); // prints 1 to 60, one integer per second
  }
}
```





