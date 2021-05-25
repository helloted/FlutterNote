# ListView顶部有空白

___



> 1

ListView头部有一段空白区域，是因为当ListView没有和AppBar一起使用时，头部会有一个padding，为了去掉padding，可以使用MediaQuery.removePadding 包裹这个ListView

`MediaQuery.removePadding(context: context,removeTop: true, child: _buildListView('aaa'))`





