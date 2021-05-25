### Flutter屏幕宽高和状态栏高度
> 1

#### 手机的物理分辨率

```
final physicalWidth = window.physicalSize.width;
final physicalHeight = window.physicalSize.height;
print('分辨率: $physicalWidth * $physicalHeight');
```

#### 手机屏幕的大小(逻辑分辨率)

```
final width = MediaQuery.of(context).size.width;
final height = MediaQuery.of(context).size.height;
```

#### 获取dpr

```
final dpr = window.devicePixelRatio;
//宽度和高度
final width = physicalWidth / dpr;
final height = physicalHeight / dpr;
print('屏幕宽高: $width * $height');
```

#### 状态栏的高度

```
final statusHeight = window.padding.top / dpr;
print('状态栏的高度: $statusHeight');
```

#### 尺寸适配

```
class SizeFit {
  static double physicalWidth;
  static double physicalHeight;
  static double dpr;
  static double screenWidth;
  static double screenHeight;
  static double statusHeight;

  static double rpx;

  static void init() {
    //1.手机的物理分辨率
    physicalWidth = window.physicalSize.width;
    physicalHeight = window.physicalSize.height;

    //2.获取dpr
    dpr = window.devicePixelRatio;

    //3.宽度和高度
    screenWidth = physicalWidth /dpr;
    screenHeight = physicalHeight /dpr;

    //4.状态栏的高度
    statusHeight = window.padding.top;

    //5.计算rpx的大小
    rpx = screenWidth / 750;
  }

  fitWidth(width) {
    return rpx * width;
  }
}
```





