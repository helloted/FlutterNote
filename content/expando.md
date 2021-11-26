# Expando


> 1

Dart 语言中也有着弱引用，它叫 `Expando<T>` 

```
class Expando<T> {
  external T operator [](Object object);
  external void operator []=(Object object, T value);
}
```

你可能会好奇上述代码弱引用体现在哪里呢？其实是在 `expando[key]=value` 这个赋值语句上。Expando 会以弱引用的方式持有 key，这里就是弱引用的地方。





