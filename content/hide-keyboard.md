# 在屏幕上任意位置点击隐藏软键盘
[How to hide soft input keyboard on flutter after clicking outside TextField/anywhere on screen?](https://stackoverflow.com/questions/51652897/how-to-hide-soft-input-keyboard-on-flutter-after-clicking-outside-textfield-anyw)

___



> 1

```dart
return GestureDetector(
      onTap: () => FocusManager.instance.primaryFocus?.unfocus(),
      child: Scaffold(
        appBar: AppBar(
          title: Text('Login'),
        ),
        body: Body(),
      ),
    );
```



