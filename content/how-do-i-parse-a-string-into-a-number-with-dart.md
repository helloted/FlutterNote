# 字符串转数字
[How do I parse a string into a number with Dart?](https://stackoverflow.com/questions/13167496/how-do-i-parse-a-string-into-a-number-with-dart)

___



> 1

```dart
var myInt = int.parse('12345');
assert(myInt is int);
print(myInt); // 12345
```

注意int.parse()接受0x开头的字符串，其他的就被认为是10进制

double.parse可以用来字符转double

```dart
var myDouble = double.parse('123.45');
assert(myDouble is double);
print(myDouble); // 123.45
```

`parse()` 会抛一个FormatException如果不能对输入的进行转换

