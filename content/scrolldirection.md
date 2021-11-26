# 监听滚动方向
> 1

```
_controller = ScrollController()
    ..addListener(() {
      upDirection = _controller.position.userScrollDirection == ScrollDirection.forward;

      // makes sure we don't call setState too much, but only when it is needed
      if (upDirection != flag) 
        setState(() {});

      flag = upDirection;
    });
```







