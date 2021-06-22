# 字符串首字母大写
[How to capitalize the first letter of a string in dart?](https://stackoverflow.com/questions/29628989/how-to-capitalize-the-first-letter-of-a-string-in-dart)

___



> 1

在版本2.6之后, dart支持extensions:

```dart
extension StringExtension on String {
    String capitalize() {
      return "${this[0].toUpperCase()}${this.substring(1)}";
    }
}
```

这样就可以直接使用

```dart
import "string_extension.dart";

var someCapitalizedString = "someString".capitalize();
```



