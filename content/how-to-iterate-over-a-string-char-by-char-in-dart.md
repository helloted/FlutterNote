# Dart中如何遍历字符串
[How to iterate over a String, char by char, in Dart?](https://stackoverflow.com/questions/9286885/how-to-iterate-over-a-string-char-by-char-in-dart)

___



> 1

```dart
"A string".runes.forEach((int rune) {
  var character=new String.fromCharCode(rune);
  print(character);
});
```

```dart
input.split('').forEach((ch) => print(ch));
```



