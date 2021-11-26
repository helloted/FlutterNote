# Future里的then vs whenComplete
[Difference between .then() and .whenCompleted() methods when working with Futures?](https://stackoverflow.com/questions/55381236/difference-between-then-and-whencompleted-methods-when-working-with-future)

___



> 1

.whenComplete 在 Future 完成后，不管是否有Error都会触发一个函数，

.then 将在 Future 完成，没有Error后触发这个函数。





