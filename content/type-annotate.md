# type 'List<dynamic>' is not a subtype of type 'List<Widget>'
[type 'List' is not a subtype of type 'List'](https://stackoverflow.com/questions/49603021/type-listdynamic-is-not-a-subtype-of-type-listwidget)

___

```dart
Widget _buildBody(BuildContext context) {
    return new StreamBuilder(
      stream: _getEventStream(),
      builder: (context, snapshot) {
        if (!snapshot.hasData) return new Text('Loading...');
        return new ListView(
          children: snapshot.data.documents.map((document) {
            return new ListTile(
              title: new Text(document['name']),
              subtitle: new Text("Class"),
            );
          }).toList(),
        );
      },
    );
  }
```

会报错

```dart
type 'List<dynamic>' is not a subtype of type 'List<Widget>'
```

> 1

问题在于类型返回的类型不是一个需要的类型，因为 `map` 后面是跟随 `toList` 没有办法提供一个type注释，解决方案是提供一个类型参数给map。

```dart
snapshot.data.documents.map<Widget>((document) {
  return new ListTile(
    title: new Text(document['name']),
    subtitle: new Text("Class"),
  );
}).toList()
```



