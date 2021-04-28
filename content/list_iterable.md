# 遍历List获得index和value
> 1

使用ForEach

```dart
var _sample = ['a','b','c'];
_sample.asMap().forEach((index, value) {

});
```

只需要index

```
list.asMap().keys.map((index) {   
    return something;
}
```

只需要value

```
list.asMap().values.map((value) {   
    return something;
}

list.map((value) {
	return 'something';
}).toList();
```

同时需要index和value

```
List list = ['a', 'b', 'c', 'd'];
List ll = list.asMap().entries.map((entry) {
   int index = entry.key;
   String value = entry.value;
   return value + index.toString();
}).toList();  


list.asMap().map((key,value) {
	return MapEntry(key, value);
}).values.toList();
```











