# 如何生成一个随机数
[How do I generate random numbers in Dart?](https://stackoverflow.com/questions/11674820/how-do-i-generate-random-numbers-in-dart)

___



> 1

使用来自`dart:math`的Random:

```
import 'dart:math';

main() {
  var rng = new Random();
  for (var i = 0; i < 10; i++) {
    print(rng.nextInt(100));
  }
}
```

> 2

 `nextInt()` 需要一个最大值. 随机数从 `0` 到最大值

```
import 'dart:math';
Random random = new Random();
int randomNumber = random.nextInt(100); // from 0 upto 99 included
```

而如果想要增加最小值

```
int randomNumber = random.nextInt(90) + 10; // from 10 upto 99 included
```







