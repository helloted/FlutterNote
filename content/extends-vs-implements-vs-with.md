# extends-vs-implements-vs-with
["extends" versus "implements" versus "with"](https://stackoverflow.com/questions/55295782/extends-versus-implements-versus-with)

___



> 1

[Extends:](https://www.dartlang.org/guides/language/language-tour#extending-a-class)

使用 extends 创建子类，使用 super 来引用超类。

Extends 是典型的 OOP 类继承。如果类 a 扩展了类 b，则在类 b 中实现的所有属性、变量、函数在类 a 中也可用。此外，可以覆盖功能等。

如果要创建类的更具体版本，请使用扩展。例如，类汽车可以扩展类汽车。在 Dart 中，一个类只能扩展一个类。

[Implements:](https://www.dartlang.org/guides/language/language-tour#implicit-interfaces)

每个类都隐式地定义了一个接口，该接口包含该类的所有实例成员及其实现的任何接口。如果要创建支持类 B 的 API 的类 A 而不继承 B 的实现，则类 A 应实现 B 接口。

如果您想创建自己的另一个类或接口的实现，则可以使用实现。当 a 类实现 b 类时。必须实现类 b 中定义的所有函数。

当您实现另一个类时，您不会从该类继承代码。您只继承类型。在 Dart 中，您可以对多个类或接口使用 implements 关键字。

[With (Mixins):](https://www.dartlang.org/guides/language/language-tour#adding-features-to-a-class-mixins)

Mixin 是一种在多个类层次结构中重用类代码的方法。

With 用于包含 Mixin。 mixin 是一种不同类型的结构，它只能与关键字 with 一起使用。





