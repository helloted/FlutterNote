# Keys的作用？
[Why are stateful widgets defined as two classes in flutter?](https://stackoverflow.com/questions/50612237/why-are-stateful-widgets-defined-as-two-classes-in-flutter)

___



> 1

什么是Keys?
Keys是Widgets的 ID。所有Widgets都有它们，而不仅仅是 StatelessWidgets。Element tree使用它们来确定Widgets是否可以重用或是否需要重建。如果未指定Keys（通常情况），则使用Widget类型来确定这一点。

为什么要使用Keys？
当Widget的数量或位置发生变化时，Keys对于维持状态很有用。如果没有Keys，那么 Flutter 框架可能会对更改的Widget感到困惑。

什么时候使用Keys？
仅在框架需要您的帮助以了解要更新哪个Widget时才使用它们。

大多数时候您不需要使用Keys。由于Keys主要仅用于维护状态，如果您有一个无状态Widget，其子部件都是无状态的，则无需在其上使用Keys。在这种情况下使用Keys不会有什么坏处，但也无济于事。

您可以使用Keys进行一些微优化。

在哪里使用Keys？
将Keys放在正在发生重新排序或添加/删除的Widget树的部分。例如，如果您要对子项是 ListTile Widget的 ListView 的项目重新排序，则将Keys添加到 ListTile Widget。

使用什么样的Keys？
Keys只是一个 ID，但您可以更改 ID 的类型。

ValueKey
ValueKey 是一个本地Key，它采用一个简单的值，如字符串或整数。

ObjectKey
如果您的Widget显示比单个值更复杂的数据，那么您可以为该Widget使用 ObjectKey。

UniqueKey
这种类型的Keys保证每次都会为您提供唯一的 ID。但是，如果您使用它，请不要将它放在 build 方法中。否则，您的Widget将永远不会具有相同的 ID，因此元素树将永远找不到要重用的匹配项。

GlobalKey
GlobalKey 可用于维护整个应用程序的状态，但请谨慎使用它们，因为它们类似于全局变量。通常最好使用状态管理解决方案。





