# 为什么用SizedBox而不是Container?
> 1

 `Container` 相比于 `SizedBox`是一个更重的Widget, 而且 `SizedBox` 有 `const` constructor.

**BAD:**

```dart
Widget buildRow() {
  return Row(
    children: <Widget>[
      const MyLogo(),
      Container(width: 4),
      const Expanded(
        child: Text('...'),
      ),
    ],
  );
}
```

**GOOD:**

```dart
Widget buildRow() {
  return Row(
    children: const <Widget>[
      MyLogo(),
      SizedBox(width: 4),
      Expanded(
        child: Text('...'),
      ),
    ],
  );
}
```





