# 单例
> 1

```
class RoomManager {
  /// 单例
  static RoomManager? _sInstance;
  static RoomManager sharedInstance() {
    if (_sInstance == null) {
      _sInstance = RoomManager();
    }
    return _sInstance!;
  }
}
```

> 2

```
class Broadcast {
  //私有构造函数
  Broadcast._internal();
  //保存单例
  static final Broadcast _singleton = Broadcast._internal();
  //工厂构造函数
  factory Broadcast() => _singleton;
}
```





