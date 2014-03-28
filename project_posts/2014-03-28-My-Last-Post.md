##Origin

Originally created in javascript, converting everything to work in Dart was actually a pleasant suprise. A large amount of javascript code actually didn't need to be touched, and while the DartEditor is not perfect, I had very few issues in my experience with this project. The biggest one was when trying to create multidimentional arrays. Dart doesn't support 2d arrays inherently, but by using preallocated Lists inside a List, it was possible to set up the matrix needed to create the nodes.


## Here's the bread and butter of Polygonz:
```
//create node matrix
    var i, j, x = 0, y = 0, nodeMatrix = new List();
    for (i = 0; i < shapeCountX+1; i++) {
        var nodeMatrixInner = new List(shapeCountY);
        for (j = 0; j < shapeCountY; j++) {
            if(i<1 || i>=shapeCountX || j<1 || j>=shapeCountY-1){
                nodeMatrixInner[j] = [x*shapeWidth, y*shapeHeight];
            }else{
                var rnd = new Random();
                nodeMatrixInner[j] = [(x+distortion*(.5-rnd.nextDouble()))*shapeWidth, (y+distortion*(.5-rnd.nextDouble()))*shapeHeight];
            }
            y=y+1;
        }
        nodeMatrix.add(nodeMatrixInner);
        x=x+1;
        y=0;
    }
```

Comparing to the javascript version:
```
//create node matrix
    var i, j, x = 0, y = 0, nodeMatrix = new Array(shapeCountX);
    for (i = 0; i < shapeCountX+1; i++) {
        nodeMatrix[i] = new Array(shapeCountY);
        for (j = 0; j < shapeCountY; j++) {
            if(i<1 || i>=shapeCountX || j<1 || j>=shapeCountY-1){
                nodeMatrix[i][j] = [x*shapeWidth, y*shapeHeight];
            }else{
                nodeMatrix[i][j] = [(x+distortion*(.5-Math.random()))*shapeWidth, (y+distortion*(.5-Math.random()))*shapeHeight];
            }
            y=y+1;
        }
        x=x+1;
        y=0;
    }
```

The same but different.
