# Flutter里的Sink和Stream
[What is the difference between Sink and Stream in Flutter?](https://stackoverflow.com/questions/50350235/what-is-the-difference-between-sink-and-stream-in-flutter)

___



> 1

`Sink` 和 `Stream` 都是 `StreamController` 的一部分。 您可以使用Sink将数据添加到StreamController，该数据可以通过Stream进行监听。 

案例

```dart
final _user = StreamController<User>();
Sink get theSink => _user.sink;
Stream<User> get theStream => _user.stream;
```

添加数据

```dart
theSink.add(yourUserObject); // This will add data to the stream.
```

监听数据

```dart
theStream.listen((user) => print(user)); 
```





