# 如何禁用一个按钮？
[How do I disable a Button in Flutter?](https://stackoverflow.com/questions/49351648/how-do-i-disable-a-button-in-flutter)

___



> 1

根据文档

"If the onPressed callback is null, then the button will be disabled and by default will resemble a flat button in the disabledColor."

```dart
 RaisedButton(
      onPressed: calculateWhetherDisabledReturnsBool() ? null : () => whatToDoOnPressed,
      child: Text('Button text')
    );
```







