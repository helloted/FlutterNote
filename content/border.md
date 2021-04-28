# 边框设置
> 1

单独设置边框

```dart
Container(
	decoration: BoxDecoration(
	   border: Border(
	       left: BorderSide(
	     	 width: 0.5,//宽度
		     color: Colors.red, //边框颜色
		   ),
	 	 ),
	 ),
)
```

四个边框一起设置

```dart
            Container(
              decoration: BoxDecoration(
                border: Border.all(
                  color: Colors.green[200], //边框颜色
                  width: 2, //宽度
                ),
              ),
            )
```





