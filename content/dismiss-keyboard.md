# 点击空白缩回键盘


> 1

Widgets是immutable不可变的，StatefulWiget继承自Widget，所以也是不可变的，把声明分为两个类就可以让StatefulWiget是不可变的同时State是可变的

```
FocusScopeNode currentFocus = FocusScope.of(context);
if (!currentFocus.hasPrimaryFocus &&
  currentFocus.focusedChild != null) {
  FocusManager.instance.primaryFocus!.unfocus();
}
```





