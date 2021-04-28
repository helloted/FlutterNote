# 如何创建一个圆角按钮？
[Create a rounded button / button with border-radius in Flutter](https://stackoverflow.com/questions/49991444/create-a-rounded-button-button-with-border-radius-in-flutter)

___



> 1

`FlatButton` 和 `RaisedButton` 已经被弃用

对于 `TextButton` and `ElevatedButton`，所以你可以用`style` 属性里的 `shape` 

圆角按钮

![img](./../images/06.jpeg)

```dart
style: ButtonStyle(
  shape: MaterialStateProperty.all<RoundedRectangleBorder>(
    RoundedRectangleBorder(
      borderRadius: BorderRadius.circular(18.0),
      side: BorderSide(color: Colors.red)
    )
  )
)
```

直角按钮

![img](./../images/07.jpeg)

```
style: ButtonStyle(
  shape: MaterialStateProperty.all<RoundedRectangleBorder>(
    RoundedRectangleBorder(
      borderRadius: BorderRadius.zero,
      side: BorderSide(color: Colors.red)
    )
  )
)
```

代码案例

```dart
Row(
  mainAxisAlignment: MainAxisAlignment.end,
  children: [
    TextButton(
      child: Text(
        "Add to cart".toUpperCase(),
        style: TextStyle(fontSize: 14)
      ),
      style: ButtonStyle(
        padding: MaterialStateProperty.all<EdgeInsets>(EdgeInsets.all(15)),
        foregroundColor: MaterialStateProperty.all<Color>(Colors.red),
        shape: MaterialStateProperty.all<RoundedRectangleBorder>(
          RoundedRectangleBorder(
            borderRadius: BorderRadius.circular(18.0),
            side: BorderSide(color: Colors.red)
          )
        )
      ),
      onPressed: () => null
    ),
    SizedBox(width: 10),
    ElevatedButton(
      child: Text(
        "Buy now".toUpperCase(),
        style: TextStyle(fontSize: 14)
      ),
      style: ButtonStyle(
        foregroundColor: MaterialStateProperty.all<Color>(Colors.white),
        backgroundColor: MaterialStateProperty.all<Color>(Colors.red),
        shape: MaterialStateProperty.all<RoundedRectangleBorder>(
          RoundedRectangleBorder(
            borderRadius: BorderRadius.zero,
            side: BorderSide(color: Colors.red)
          )
        )
      ),
      onPressed: () => null
    )
  ]
)
```

