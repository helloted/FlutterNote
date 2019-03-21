# 类方法与实例方法
1. 静态成员和静态方法

```dart
class A{
  static String helloworld='helloworld';

  void say(){
    print(helloworld);
  }
  
  static void push(){
    print('push');
  }
  
}

void main(){
  print(A.helloworld);// 静态变量直接调用
  
  A a=new A();
  a.say(); //实例方法必须先实例对象
  
  A.push() // 静态方法直接调用
}
```

1. 静态变量helloworld可以通过外部直接访问，不需要将A类实例化。
2. 静态方法push可以直接外部引用，不需要将A类实例化。
3. a.helleworld是错误访问，因为静态变量不是在实例中，是在类中。同理静态方法也是。

