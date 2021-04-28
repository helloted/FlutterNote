# 双问号??的用途
[What are the ?? double question marks in Dart?](https://stackoverflow.com/questions/54031804/what-are-the-double-question-marks-in-dart)

___



> 1

 `??` 意思是“如果为null？”

```dart
String a = b ?? 'hello';
```

意味着a=b，但是如果b是null那么a='hello'

另外一个运算符是 `??=`. 

```dart
b ??= 'hello';
```

表示如果 `b` 是null 给它赋值`hello`.否则的话，则不变

**Reference**

- [A Tour of the Dart Language: Operators](https://www.dartlang.org/guides/language/language-tour#operators)
- [Null-aware operators in Dart](http://blog.sethladd.com/2015/07/null-aware-operators-in-dart.html)

**Terms**

- `??` -- if null operator
- `??=` -- null-aware assignment
- `x?.p` -- null-aware access
- `x?.m()` -- null-aware method invocation





