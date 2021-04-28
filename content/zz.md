# 问题？
[Why are stateful widgets defined as two classes in flutter?](https://stackoverflow.com/questions/50612237/why-are-stateful-widgets-defined-as-two-classes-in-flutter)

___



> 1

Widgets是immutable不可变的，StatefulWiget继承自Widget，所以也是不可变的，把声明分为两个类就可以让StatefulWiget是不可变的同时State是可变的





