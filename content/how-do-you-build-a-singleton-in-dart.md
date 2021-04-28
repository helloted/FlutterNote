# Dart中怎么创建一个单例？

[How do you build a Singleton in Dart?](https://stackoverflow.com/questions/12649573/how-do-you-build-a-singleton-in-dart)



> 1

鉴于 Dart's [factory constructors](https://www.dartlang.org/guides/language/language-tour#factory-constructors), 可以很轻易创建一个单例

```
class Singleton {
  static final Singleton _singleton = Singleton._internal();

  factory Singleton() {
    return _singleton;
  }

  Singleton._internal();
}
```

你可以这样构建

```
main() {
  var s1 = Singleton();
  var s2 = Singleton();
  print(identical(s1, s2));  // true
  print(s1 == s2);           // true
}
```

> 2

1、工厂模式

```dart
class SingletonOne {

  SingletonOne._privateConstructor();

  static final SingletonOne _instance = SingletonOne._privateConstructor();

  factory SingletonOne() {
    return _instance;
  }
}

SingletonOne one = SingletonOne();
```

2、静态变量getter

```
class SingletonTwo {

  SingletonTwo._privateConstructor();

  static final SingletonTwo _instance = SingletonTwo._privateConstructor();

  static SingletonTwo get instance => _instance;
}

SingletonTwo two = SingletonTwo.instance;
```

3、静态变量

```
class SingletonThree {

  SingletonThree._privateConstructor();

  static final SingletonThree instance = SingletonThree._privateConstructor();
}

SingletonThree three = SingletonThree.instance;
```

