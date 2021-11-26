# 怎么取消延迟操作？
[How do I cancel Future.delayed?](https://stackoverflow.com/questions/56119923/how-do-i-cancel-future-delayed)

___



> 1

使用Timer

```dart
 Timer t = Timer(Duration(seconds: myDuration), () {
    checkAnswer('');
    jumpToNextQuestion();
  });
  // and later, before the timer goes off...
  t.cancel();
```





