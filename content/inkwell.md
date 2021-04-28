# InkWell水波纹效果
___



> 1

InkWell组件在用户点击时出现“水波纹”效果，InkWell简单用法：

```
InkWell(
        onTap: (){},
        child: Text('这是InkWell点击效果'),
      )
```

`onTap`是点击事件回调，如果不设置无法出现“水波纹”效果，效果如下：

![img](http://img3.sycdn.imooc.com/5e566e3c0001656a02580086.jpg)

设置水波纹颜色：

```
InkWell(
	onTap: () {},
	splashColor: Colors.red,
	...
)
```

效果如下：

![img](http://img4.sycdn.imooc.com/5e566e3c0001555c03440093.jpg)

设置高亮颜色颜色：

```
InkWell(
	onTap: () {},
	highlightColor: Colors.blue,
	...
)
```

高亮颜色是按住时显示的颜色，效果如下：

![img](http://img1.sycdn.imooc.com/5e566e3d0001b68703270075.jpg)

给字体添加边距和圆角边框，扩大“水波纹”效果：

```
InkWell(
        onTap: (){},
        child: Container(
          padding: EdgeInsets.symmetric(horizontal: 20,vertical: 8),
          decoration: BoxDecoration(
            border:Border.all(color: Colors.blue),
            borderRadius: BorderRadius.all(Radius.circular(30))
                
          ),
          child: Text('这是InkWell点击效果'),
        ),
      )
```

效果如下：

![img](http://img2.sycdn.imooc.com/5e566e3d0001116703480096.jpg)







