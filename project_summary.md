# Polygonz - Beautifully Algorithmic Backgrounds

## Zauce Technologies
- Zach Nagengast github.com/ZachNagengast
- Live Demo: www.zaucetech.com/polygonz

## Description

Polygonz is a tool that creates beautiful and customizable polygon-styled backgrounds for your devices or webpages, algorithmically, built with Dart. It was inspired by a design trend which I will descripe as polygon design. I thought the style looked really neat and wanted to do something in this area. 

![Main inspiration](project_images/inspiration.png?raw=true "Samsung S5")

With the launch of the S5, I was inspired to take action with this project. I loved this background, but wanted to customize it and make my own, which until now could only be done with photoshop. So I put my head down and after a while came up with this, hope you enjoy.

## Links

[Live Demo](www.zaucetech.com/polygonz)
[Main Repo (feel free to fork!)](http://www.github.com/ZachNagengast/polygonz)
[Pure Javascript Prototype Repo](https://github.com/ZachNagengast/polygonz/tree/javascript)
[First Version Demo (before name change)](http://zaucetech.com/fragmenter)
[Initial reddit post & ideas](http://www.reddit.com/r/javascript/comments/1zdje7/need_a_new_background_image_make_one_yourself/)


## Example Code
Polygonz creates a matrix of nodes and then loops through them to draw the triangles. This allows for future possibilities such as squares and other various patterns. Code below show how the matrix is made in Dart.

Html
```
<canvas id="canvas"></canvas>
```

Dart
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
    
    var canvas = document.getElementById("canvas");
    //setup the canvas
    canvas.width = canvasWidth;
    canvas.height = canvasHeight;
    
    //draw the image
    drawImage(nodeMatrix);
    
    print("Updarted");
```

## Links to External Libraries

[Main Repo (feel free to fork!)](http://www.github.com/ZachNagengast/polygonz)



## Images & Videos
Various demos and inspirations

![iPad Demo](project_images/ipad.png?raw=true "iPad Demo")
![iPhone Demo](project_images/iphone.png?raw=true "iPhone Demo")
