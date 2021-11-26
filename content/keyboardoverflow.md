# 键盘弹出后高度超出屏幕
___



> 1

加入以下属性

```
Scaffold(
	resizeToAvoidBottomPadding: false, //输入框抵住键盘
)
```

是否自动调整body属性控件的大小，以避免脚手架底部被覆盖。例如，如果在脚手架上方显示屏幕键盘，则可调整body属性控件的大小以避免被键盘覆盖。如果你不需要此功能，可以将resizeToAvoidBottomPadding属性设置为false





