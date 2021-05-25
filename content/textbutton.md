# TextButton
```
  //这是一个文本按钮 未设置点击事件下的样式
  Widget buildTextButton2() {
    return TextButton(
      child: Text("TextButton按钮"),
      //添加一个点击事件
      onPressed: () {},
      //设置按钮是否自动获取焦点
      autofocus: true,
      //定义一下文本样式
      style: ButtonStyle(
        //定义文本的样式 这里设置的颜色是不起作用的
        textStyle: MaterialStateProperty.all(
            TextStyle(fontSize: 18, color: Colors.red)),
        //设置按钮上字体与图标的颜色
        //foregroundColor: MaterialStateProperty.all(Colors.deepPurple),
        //更优美的方式来设置
        foregroundColor: MaterialStateProperty.resolveWith(
          (states) {
            if (states.contains(MaterialState.focused) &&
                !states.contains(MaterialState.pressed)) {
              //获取焦点时的颜色
              return Colors.blue;
            } else if (states.contains(MaterialState.pressed)) {
              //按下时的颜色
              return Colors.deepPurple;
            }
            //默认状态使用灰色
            return Colors.grey;
          },
        ),
        //背景颜色
        backgroundColor: MaterialStateProperty.resolveWith((states) {
          //设置按下时的背景颜色
          if (states.contains(MaterialState.pressed)) {
            return Colors.blue[200];
          }
          //默认不使用背景颜色
          return null;
        }),
        //设置水波纹颜色
        overlayColor: MaterialStateProperty.all(Colors.yellow),
        //设置阴影  不适用于这里的TextButton
        elevation: MaterialStateProperty.all(0),
        //设置按钮内边距
        padding: MaterialStateProperty.all(EdgeInsets.all(10)),
        //设置按钮的大小
        minimumSize: MaterialStateProperty.all(Size(200, 100)),

        //设置边框
        side:
            MaterialStateProperty.all(BorderSide(color: Colors.grey, width: 1)),
        //外边框装饰 会覆盖 side 配置的样式
        shape: MaterialStateProperty.all(StadiumBorder()),
      ),
    );
  }

```

