# Gesturedetector空白点击
[How to make GestureDetector also work when touch empty space in Flutter](https://stackoverflow.com/questions/59062264/how-to-make-gesturedetector-also-work-when-touch-empty-space-in-flutter)

___



> 1

可以使用属性：behavior: HitTestBehavior.opaque

```
GestureDetector(
                behavior: HitTestBehavior.opaque,
                child: Container(
                  child: Hero(
                    tag: 'test',
                    child: Column(
                      crossAxisAlignment: CrossAxisAlignment.start,
                      children: <Widget>[
                        Text('Very very very long long long long text view'),
                        SizedBox(height: 10),
                        Text('Short text')
                      ],
                    ),
                  ),
                ),
                onTap: () {
                  print('Tapped');
                },
              ),

```







