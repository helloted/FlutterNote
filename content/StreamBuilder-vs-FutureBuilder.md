# StreamBuilder vs FutureBuilder
[Flutter StreamBuilder vs FutureBuilder](https://stackoverflow.com/questions/50844519/flutter-streambuilder-vs-futurebuilder)

___



> 1

StreamBuilder 和 FutureBuilder 都有相同的行为：它们监听各自对象的变化。并在收到新值通知时触发新build。

所以归根结底，他们的不同之处在于他们所听对象的工作方式。

Future 就像 JS 中的 Promise 或 C# 中的 Task。它们是异步请求的表示。Future只有一种响应。 Future 的一个常见用法是处理 HTTP 调用。你可以在 Future 上听到的是它的状态。无论是完成、成功完成还是出现错误。但就是这样。

另一方面，Stream 就像 JS 中的异步迭代器。这可以被同化为一个可以随时间变化的值。它通常是websockets或事件（例如点击）的表示。通过收听 Stream，您将获得每个新值，以及 Stream 是否有错误或已完成。





