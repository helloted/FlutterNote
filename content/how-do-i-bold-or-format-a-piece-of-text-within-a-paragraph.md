# 如何在一段文字内有多个字体格式
[How do I bold (or format) a piece of text within a paragraph?](https://stackoverflow.com/questions/41557139/how-do-i-bold-or-format-a-piece-of-text-within-a-paragraph)

___



> 1

 可以用[RichText](https://docs.flutter.io/flutter/widgets/RichText-class.html)

```dart
var text = new RichText(
  text: new TextSpan(
    // Note: Styles for TextSpans must be explicitly defined.
    // Child text spans will inherit styles from parent
    style: new TextStyle(
      fontSize: 14.0,
      color: Colors.black,
    ),
    children: <TextSpan>[
      new TextSpan(text: 'Hello'),
      new TextSpan(text: 'World', style: new TextStyle(fontWeight: FontWeight.bold)),
    ],
  ),
 );
```

结果就是Hello **World**