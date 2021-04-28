# 如何设设置背景图片？
[How do I Set Background image in Flutter?](https://stackoverflow.com/questions/44179889/how-do-i-set-background-image-in-flutter)

___



> 1

可以使用 [`DecorationImage`](https://docs.flutter.io/flutter/painting/DecorationImage-class.html) 和 [`BoxFit.cover`](https://docs.flutter.io/flutter/painting/BoxFit-class.html).

```dart
class BaseLayout extends StatelessWidget{
  @override
  Widget build(BuildContext context){
    return Scaffold(
      body: Container(
        decoration: BoxDecoration(
          image: DecorationImage(
            image: AssetImage("assets/images/bulb.jpg"),
            fit: BoxFit.cover,
          ),
        ),
        child: null /* add child content here */,
      ),
    );
  }
}
```







