# Dart里怎么创建私有变量？
[How to create private variables in Dart?](https://stackoverflow.com/questions/17488611/how-to-create-private-variables-in-dart)

___



> 1

来自 Dart 文档：

与 Java 不同，Dart 没有关键字 public、protected 和 private。 如果标识符以下划线 _ 开头，则它对library是私有的。

library不仅提供 API，而且是一个隐私单元：以下划线 _ 开头的标识符仅在库内部可见。







