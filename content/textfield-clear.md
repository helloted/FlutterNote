# TextField添加清除按钮
[How to add clear button to TextField Widget](https://stackoverflow.com/questions/48927928/how-to-add-clear-button-to-textfield-widget)

___



> 1

创建一个controller

```dart
var _controller = TextEditingController();
```

```dart
TextField(
  controller: _controller,
  decoration: InputDecoration(
    hintText: 'Enter a message',
    suffixIcon: IconButton(
      onPressed: _controller.clear,
      icon: Icon(Icons.clear),
    ),
  ),
)
```



