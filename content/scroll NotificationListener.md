# ScrollView滚动监听
1、通过通知

```dart
NotificationListener<ScrollNotification>(
  child: ListView.builder(
    itemCount: 50,
    itemBuilder: (BuildContext context, int index) {
      return Container(
        height:50 ,
        child: Center(
          child: Text('$index'),
        ),);
    },
  ),
  onNotification: (ScrollNotification scrollInfo) {
    if (scrollInfo.metrics.pixels ==
        scrollInfo.metrics.maxScrollExtent) {
      print(scrollInfo);
    }
  },
),
```

2、通过ScrollController

```
   ScrollController _listViewScrollController = ScrollController(); //listview的控制器
   
   _listViewScrollController.addListener(() {
      print('正在滑动');
      print(_listViewScrollController.offset);
      if (_listViewScrollController.position.pixels ==
          _listViewScrollController.position.maxScrollExtent) {
        print('滑动到了最底部');

      }
    });
    
    
    ListView.builder(
    											controller:_listViewScrollController
                          itemCount: 50,
                          itemBuilder: (BuildContext context, int index) {
                            return Container(
                              height:50 ,
                              child: Center(
                                child: Text('$index'),
                              ),);
                          },
                        ),
```

