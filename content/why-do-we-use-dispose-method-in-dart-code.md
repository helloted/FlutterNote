# 问题？
[Why do we use dispose() method in dart code?](https://stackoverflow.com/questions/59558604/why-do-we-use-dispose-method-in-dart-code)

___



> 1

dispose 方法用于在移除state对象时释放分配给变量的内存。

例如，如果您在应用程序中使用stream，则必须释放分配给 streamController 的内存。 否则，会造成内存泄露。



> 2

主要目的是获得callback，您可以在其中释放所有资源。

如果您已初始化State中的任何资源，则在处理该State时关闭或销毁该资源非常重要。

例如：如果您在 StatefullWidget 的 initState 中创建stream，那么在该状态的 dispose 方法中关闭该stream很重要，否则会导致内存泄漏。







