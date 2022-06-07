## Introduction to HTML5 Canvas API

Canvas API is used to create graphics and animations using Javascript in webpage. Few of the interesting examples built using canvas API are shown below:-


- [Animated background](https://codepen.io/MarcoGuglielmelli/pen/ExGYae)
- [Hexagon Pattern](https://codepen.io/towc/pen/mJzOWJ)
- [Falling Hearts](https://codepen.io/at80/pen/kyOdeK)

Today we are going to explore the basics on Canvas API and learn how to create graphics using this API.

- Canvas Element      
We make use of `<canvas>` HTML tag to create a container for HTML5 graphics. The first thing which we can do to create graphics using canvas is to insert this tag in our webpage as shown below:


```javascript
...
<body>
<canvas id="myCanvas"></canvas>
</body>
```

We specify `id` in canvas since we need to access to canvas tag in Javascript. Next we insert a new script file in within `scripts` folder in our project and add reference to it our page:-
```javascript
...
<body>
<canvas id="myCanvas"></canvas>
<script src="scripts/canvasExample.js"></script>
</body>
```

In the `canvasExample.js` file we first make a reference to canvas tag using below code:-

```
const canvas = document.getElementById('myCanvas');
```
Next, the `HTMLCanvasElement.getContext()` method gets that element's `context`—the thing onto which the graphic will be rendered. We can get context on `2d` plane using `getContext('2d')` option as shown below:-

```
const ctx = canvas.getContext('2d');
```
For `3d` plane we can make use of `webgl` parameter in context option. We are going to use the `ctx` variable to draw graphics in the rest of the article.

Next we can start off into drawing actual graphics like rectangles or lines as shown below:-


-  Drawing rectangle on canvas:-

```
ctx.fillStyle = 'rgb(100, 150,200)';
ctx.fillRect(50,50,150,100);
```

Preview:-

![Screenshot 2022-06-06 at 8.36.07 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1654527972771/2y-YeVnnd.png align="left")

Here the first two parameters in `fillRect` method are used to starting top-left coordinate for the rectangle and next two params specify the width and height of the rectangle.

 
- Drawing lines on canvas:   
For drawing lines we need to specify the starting and ending coordinate using two different methods.
We first use `moveTo` method to specify starting co-ordinate and `lineTo` for specifying ending coordinate. Finally `stroke` method is used to draw the line.

```
ctx.moveTo(60,60);
ctx.lineTo(200,200);
ctx.stroke();
```
Preview:-
![Screenshot 2022-06-06 at 8.55.36 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1654529140783/ueNmwy9-k.png align="left")

- Drawing text on the canvas       
For drawing text we can use `fillText` method as shown below:-
```
ctx.font = "30px Arial";
ctx.fillText("Hello World", 10, 50);
```

Preview:-

![Screenshot 2022-06-06 at 8.59.14 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1654529358696/piaUZhfg9.png align="left")

That's it from my end for today. See you all in the next article.



