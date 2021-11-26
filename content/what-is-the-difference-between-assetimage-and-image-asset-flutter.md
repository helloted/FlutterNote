# Image.asset和AssetImage的区别
[What is the difference between AssetImage and Image.asset - Flutter](https://stackoverflow.com/questions/53309622/what-is-the-difference-between-assetimage-and-image-asset-flutter)

___



> 1

`Image` 是一个 `StatefulWidget` ，然后 `Image.asset` 一个命名构造函数，你可以直接在你的Widget tree使用它。

`AssetImage` 是一个 `ImageProvider` ，它负责获取指定路径的图像。





