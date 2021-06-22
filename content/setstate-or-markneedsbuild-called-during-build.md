# build期间调用setState或者markNeedsBuild出错
[setState() or markNeedsBuild called during build](https://stackoverflow.com/questions/47592301/setstate-or-markneedsbuild-called-during-build)

___



> 1

在build方法往完全处理完成之前调用setState时会报错的，可以用下面的方法

```dart
WidgetsBinding.instance.addPostFrameCallback((_){

  // Add Your Code here.

});
```

或者

```dart
SchedulerBinding.instance.addPostFrameCallback((_) {

  // add your code here.

  Navigator.push(
        context,
        MaterialPageRoute(
            builder: (context) => NextPage()));
});
```





