# StatefulWidget为什么要定义为两个类？
[Why are stateful widgets defined as two classes in flutter?](https://stackoverflow.com/questions/50612237/why-are-stateful-widgets-defined-as-two-classes-in-flutter)

___



> 1

- Widgets是immutable不可变的，StatefulWiget继承自Widget，所以也是不可变的，把声明分为两个类就可以让StatefulWiget是不可变的同时State是可变的
- Widgets是通过`new MyWidget()`方法来实例化的，如果我们把两个类合为一个类，每次更新都要通过`new MyWidget()`来重置State的每个属性

State如果想要获取对应Widget的属性，可以通过this.widget来获取





