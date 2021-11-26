# Flutter滚动组件添加滚动条
> 1

默认情况下，Flutter 的滚动组件（比如 ListView）没有显示滚动条，使用 **Scrollbar** 显示滚动条：

```text
Scrollbar(
  child: ListView.builder(
    reverse: false,
    itemBuilder: (BuildContext context, int index) {
      return Card(
        child: Container(
          height: 45,
          alignment: Alignment.center,
          child: Text('$index'),
        ),
      );
    },
    itemCount: 30,
    itemExtent: 50,
  ),
)
```

修改颜色使用

```dart
child: RawScrollbar(
                    thumbColor: Colors.redAccent,
                    radius: Radius.circular(20),
                    thickness: 5,
                    child: //scrollable widget
                   )
```



