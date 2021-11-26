# 多个任务完成后再执行操作


> 1

Future.wait可以实现多个任务后再执行操作

```dart
Future.wait([
  // 2秒后返回结果  
  Future.delayed(new Duration(seconds: 2), () {
    return "hello";
  }),
  // 4秒后返回结果  
  Future.delayed(new Duration(seconds: 4), () {
    return " world";
  })
]).then((results){
  print(results[0]+results[1]);
}).catchError((e){
  print(e);
});
```

会在4秒后打印结果helloworld



