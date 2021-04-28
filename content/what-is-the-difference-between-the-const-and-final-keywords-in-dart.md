# const和final的区别

[What is the difference between the “const” and “final” keywords in Dart?](https://stackoverflow.com/questions/50431055/what-is-the-difference-between-the-const-and-final-keywords-in-dart)

> 1

### Const

值必须在编译时就已知 ***compile-time***, `const birthday  = "2008/12/25"`
初始化后不可变更

------

### Final

值在运行时已知 ***run-time***, `final birthday = getBirthDateFromDB()`
初始化后不可变更

> 2

**Const:**
如果值是在运行时才得到 (`new DateTime.now()`, for example), 你不能使用 const，然而如果值是在编译时就已知 (`const a = 1;`), 那你应该用 `const` 而不是 `final`. 还有两个不同在 `const` 和 `final`之间，首先，如果你使用 `const`, 你最好声明是 `static const` 而不仅仅 `const`. 其次，如果你有一个 `const` 集合，里面所有元素都是 `const`. 如果你有一个 `final` 集合, 里面的元素不一定是 `final`.

**Final:**
编译时不知道值，运行时才知道值，那应该用`final` 