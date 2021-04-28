### 怎么移除Flutter的debug标志？

[How to remove the Flutter debug banner?](https://stackoverflow.com/questions/48893935/how-to-remove-the-flutter-debug-banner)

___



> 1

 `MaterialApp` 内设置 `debugShowCheckedModeBanner` 为 `false`.

```
MaterialApp(
  debugShowCheckedModeBanner: false,
)
```

debug标志在release版本内会自动移除



