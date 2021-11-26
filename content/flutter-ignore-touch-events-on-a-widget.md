# 忽略Touch事件
[Flutter: Ignore touch events on a Widget](https://stackoverflow.com/questions/50600747/flutter-ignore-touch-events-on-a-widget)

___



> 1

- **`IgnorePointer`**

  ```dart
  IgnorePointer(
    child: ElevatedButton(
      onPressed: () {},
      child: Text('Not clickable Button'),
    ),
  );
  ```

- **`AbsorbPointer`**

  ```dart
  AbsorbPointer(
    child: ElevatedButton(
      onPressed: () {},
      child: Text('Not clickable Button'),
    ),
  );
  ```

------

**区别在哪?**

`IgnorePointer` 只会忽略child的点击事件，不影响点击链上其他接收点击事件

 `AbsorbPointer` 会阻止整个touch事件

```dart
@override
  Widget build(BuildContext context) {
    return Scaffold(
			body: SizedBox(
      width: double.infinity,
      child: Stack(
        children: <Widget>[
          Positioned(
            left: 0,
            width: 250,
            child: ElevatedButton(
              // color: Colors.red,
              onPressed: () => print("Button 1"),
              child: Text("Button 1"),
            ),
          ),
          Positioned(
            right: 0,
            width: 250,
            child: AbsorbPointer( // replace this with AbsorbPointer and button 1 won't receive click
              child: ElevatedButton(
                onPressed: () => print("Button 2"),
                child: Text("Button 2"),
              ),
            ),
          ),
        ],
      ),
    ),);
  }
```





