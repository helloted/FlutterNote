# Isolate vs Future？
[Flutter Isolate vs Future](https://stackoverflow.com/questions/52498773/flutter-isolate-vs-future)

___



> 1

Future是一个操作：在异步执行完成后得到通知，异步执行使用event queue，代码在同一个线程内并发执行。

https://webdev.dartlang.org/articles/performance/event-loop

Dart代码默认执行在root isolate.

你可以开启一个额外的isolates(运行在其他线程)，一个isolate可以被root isolate相同Dart代码加载或使用不同的Dart代码（从某些Dart文件或URL加载）

每个isolate有独立的内存和event loop.

