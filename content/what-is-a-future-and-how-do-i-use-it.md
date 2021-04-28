# Future是什么？怎么用？
[What is a Future and how do I use it?](https://stackoverflow.com/questions/63017280/what-is-a-future-and-how-do-i-use-it)

___



> 1

文档 [documentation](https://api.flutter.dev/flutter/dart-async/Future-class.html) :

> An object representing a delayed computation.
>
> 表示延迟处理(计算)的对象。

Future就是用来作为异步处理的对象

这是通过一种称为“模式”的方式来实现的 [async](https://stackoverflow.com/questions/tagged/async) 和 [wait](https://stackoverflow.com/questions/tagged/await)。由于花费一些时间的方法无法立即返回，因此它将返回完成时传递值的承诺。

那就是所谓的`Future`。`Future<T>`是将来会给您带来收益的东西。

让我们尝试不同的解释：

> future表示异步操作的结果，并且可以具有两种状态：未完成或已完成。

最有可能的是，由于您这样做并不是为了好玩，实际上，您需要获得结果`Future`才能在您的应用程序中进行。您需要显示数据库中的号码或找到的电影列表。因此，您要等待，直到结果出现为止。这是`await`进来的地方：

```dart
Future<List<Movie>> result = loadMoviesFromSearch(input); // cost time

// right here, you need the result. So you wait for it:
List<Movie> movies = await result;
```

但是，您只能`await`在本身被标记为的函数中使用关键字`async`并返回`Future`。因为当您执行`await`某些操作时，正在等待的函数将无法立即返回其结果。您只能退还所拥有的东西，如果您必须等待，则必须退还承诺以在以后交付。

```dart
Future<Pizza> getPizza() async {
    Future<PizzaBox> delivery = orderPizza();        

    var pizzaBox = await delivery;

    var pizza = pizzaBox.unwrap();
    
    return pizza;   
}
```

我们的getPizza函数必须*等待*比萨饼，因此`Pizza`，它必须立即返回*将来将有*披萨饼的承诺，而不是立即返回。现在，您可以依次`await`在某处获取getPizza函数。

# 如何在Flutter中将Future与窗口小部件一起使用？

flutter中的所有小部件都期望真实值。当按钮需要文本时，它不能保证以后会出现文本。它需要显示的按钮*现在*，所以它需要的文本*现在*。

但是有时候，您所拥有的只是一个`Future`。那就[`FutureBuilder`](https://api.flutter.dev/flutter/widgets/FutureBuilder-class.html)来了。您可以在有未来时使用它，在等待时显示一件事（例如进度指示器），在完成时显示另一件事（例如结果）。

让我们看一下我们的披萨示例。您想订购披萨，想要在等待时显示进度指示器，想要在交货后查看结果，并且可能在出现错误时显示错误消息：

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

/// ordering a pizza takes 5 seconds and then gives you a pizza salami with extra cheese
Future<String> orderPizza() {
  return Future<String>.delayed(Duration(seconds: 5), () async => 'Pizza Salami, Extra Cheese');
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      theme: ThemeData.dark(),
      home: Scaffold(
        body: Center(
          child: PizzaOrder(),
        ),
      ),
    );
  }
}

class PizzaOrder extends StatefulWidget {
  @override
  _PizzaOrderState createState() => _PizzaOrderState();
}

class _PizzaOrderState extends State<PizzaOrder> {
  Future<String> delivery;

  @override
  Widget build(BuildContext context) {
    return Column(
        crossAxisAlignment: CrossAxisAlignment.center,
        mainAxisAlignment: MainAxisAlignment.spaceEvenly,
        children: [
          RaisedButton(
            onPressed: delivery != null ? null : () => setState(() { delivery = orderPizza(); }),
            child: Text('Order Pizza Now')
          ),
          delivery == null
            ? Text('No delivery scheduled')
            : FutureBuilder(
              future: delivery,
              builder: (context, snapshot) {
                if(snapshot.hasData) {
                  return Text('Delivery done: ${snapshot.data}');
                } else if(snapshot.hasError) {
                  return Text('Delivery error: ${snapshot.error.toString()}');
                } else {
                  return CircularProgressIndicator();
                }
              })
        ]);
  }
}
```

这是您使用FutureBuilder来显示未来结果的方式。



