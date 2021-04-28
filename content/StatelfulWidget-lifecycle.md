# StatefulWidget的生命周期
[What is the relation between stateful and stateless widgets in Flutter?](https://stackoverflow.com/questions/47501710/what-is-the-relation-between-stateful-and-stateless-widgets-in-flutter)



1、**createState()** -- 当Flutter一开始创建StatefulWidget, 会立刻调用 `createState()`.

- 在tree给定位置为此Widget创建可变State。
- 子类应重写此方法以返回其关联的State子类的新创建的实例：

```dart
@override
_MyState createState() => _MyState();
```

2、**mounted == true** -- 所有Widget都具有`this.mount`布尔属性。 当开始buildContext时，它变为true。 卸载Widget时调用`setState`是错误的，不管 此State对象当前是否在树中。

- 在创建State对象之后，在调用`initState`之前，framework将State对象与   `BuildContext`关联。 状态对象会一直保持直到调用`dispose（）`，在此之后，framework将不再询问再次建立状态对象。 
- 除非mounted为true，否则调用setState是错误的。 

```dart
bool get mounted => _element != null;
```

3、**initState()** -- Widget创建之后第一个调用的方法 (after the class constructor, of course.)

`initState` 会被调用一次且仅有一次，它必须调用 `super.initState()`.

- 初始化数据依赖于特定BuildContext的Widget创建实例的数据。

- 初始化属性依赖于树中“父”Widget的属性。

- Subscribe to Streams，ChangeNotifiers或任何其他可能更改此Widget的数据的对象。

```dart
@override
initState() {
  super.initState();
  // Add listeners to this class
  cartItemStream.listen((data) {
    _updateWidget(data);
  });
}
```

4、**didChangeDependencies()** -- 当此State对象的依赖项更改时调用。

- 这个方法在 `initState`之后立刻调用，在这个方法里可以安全调用`BuildContext.inheritFromWidgetOfExactType`
- 子类很少重写此方法，因为framewokr总是在依赖项更改后调用build。 某些子类确实重写了此方法，因为当它们的依赖项发生变化时，它们需要做一些昂贵的工作（例如，网络获取），并且对于每个build而言，所做的工作都太昂贵了。

```dart
@protected
@mustCallSuper
void didChangeDependencies() { }
```

5、**build()** -- 描述Widget代表的用户界面部分。

Framework 会在下面情形下调用这个方法：

- 调用了 `initState`.
- 调用了 `didUpdateWidget`.
- 接受了一个 `setState`.
- 在此State对象的依存关系发生更改之后（例如，之前的build所引用的InheritedWidget发生了更改）。
- 调用deactivate()后，然后将State对象重新插入到另一个位置的树中。

```dart
@override
  Widget build(BuildContext context, MyButtonState state) {
    ... () { print("color: $color"); } ...
  }
```

6、**didUpdateWidget()** -- 每当Widgt配置更改时调用。

- 如果父Widget重建并请求更新树中的该位置以显示具有相同运行时类型和Widget.key的新Widget，则框架将更新此State对象的Widget属性以引用新Widget，然后调用使用前一个Widget作为参数的此方法。
- 重写此方法以在Widget更改时做出响应（例如，开始隐式动画）。
- 框架总是在调用didUpdateWidget之后调用build，这意味着在didUpdateWidget中对setState的任何调用都是多余的。

```dart
@mustCallSuper
@protected
void didUpdateWidget(covariant T oldWidget) { }
```

7、**setState()** -- 每当您更改State对象的内部状态时，都要在传递给setState的函数中进行更改.

- 调用 setState 通知框架该对象的内部状态已更改，该方式可能会影响此子树中的用户界面，从而导致框架为这个State对象build。
- 如果仅在不调用setState的情况下直接更改状态，则框架可能不会安排build，并且可能不会更新此子树的UI以反映新状态。

```dart
setState(() { _myState = newValue });
```

8、**deactivate()** -- 当从树中删除State时，将调用Deactivate，但是可以在当前帧更改完成之前将其重新插入。 之所以存在此方法，是因为状态对象可以从树中的一个点移动到另一点。

每当框架从树中删除此State对象时，框架都会调用此方法。 在某些情况下，框架会将State对象重新插入到树的另一部分（例如，如果包含该State对象的子树从树中的一个位置移植到另一个位置）。 如果发生这种情况，框架将确保它调用build以使State对象有机会适应其在树中的新位置。 如果框架确实重新插入了此子树，则它将在从子树中删除该子树的动画帧结束之前执行此操作。 因此，状态对象可以推迟释放大多数资源，直到框架调用其dispose方法为止。

> - The framework calls this method whenever it removes this State object from the tree. In some cases, the framework will reinsert the State object into another part of the tree (e.g., if the subtree containing this State object is grafted from one location in the tree to another). If that happens, the framework will ensure that it calls build to give the State object a chance to adapt to its new location in the tree. If the framework does reinsert this subtree, it will do so before the end of the animation frame in which the subtree was removed from the tree. For this reason, State objects can defer releasing most resources until the framework calls their dispose method.

这个很少用到

```dart
@protected
@mustCallSuper
void deactivate() { }
```

9、**dispose()** -- 从树中永久删除此对象时调用。

- 当此State对象不会再次bulid时，框架将调用此方法。 在框架调用dispose之后，状态对象被认为是未接入的，并且mounted属性为false。 此时调用setState是错误的。 生命周期的这一阶段是终极阶段：无法重新嵌入已dispose的State对象。
- 子类应重写此方法以释放此对象保留的所有资源（例如，停止任何活动的动画）。

```dart
@protected
@mustCallSuper
void dispose() {
  assert(_debugLifecycleState == _StateLifecycle.ready);
  assert(() { _debugLifecycleState = _StateLifecycle.defunct; return true; }());
}
```

[![enter image description here](https://i.stack.imgur.com/zzElL.png)](https://i.stack.imgur.com/zzElL.png)

