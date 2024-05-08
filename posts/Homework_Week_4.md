---
title: Week 4 
published_at: 2024-04-3
snippet: Notes and Homework from Week 4 Class
disable_html_sanitization: true
---

###Create and post a fractal to your blog using recursion and Canvas API.

###Document your process, discussing the resources you used and problems you encountered.

###Can this method be used to maximize chaos?  How might you use it in your A2?

```html
<html>
<head>
	<script type="application/javascript">
	function draw(val=1) {
		var canvas = document.getElementById('canvas');
		if (canvas.getContext) {
			var ctx = canvas.getContext("2d");
			ctx.clearRect(0, 0, canvas.width, canvas.height);
			drawT(); //Trait around the canvas (black border)
			drawF(val); //draw Fractal
		}
		function drawF(step,color=null)
		{
			var toDraw=false; //Color management variable to separate 4 transformations
			if (step > 0)
			{
				if(color) { toDraw=true; }
				step = step-1;
				ctx.save();
        
				ctx.transform(0.5, 0, 0, 0.5, 250,0);
				ctx.rotate(90*Math.PI/180);
				if(toDraw) { ctx.fillStyle=color; }
				else { ctx.fillStyle="#FF0000"; color="#FF0000"; }
	
				drawF(step, color);
				ctx.restore();

				ctx.save();
				ctx.transform(0.5, 0, 0, 0.5, 250, 0);
				ctx.scale(-1, 1);
				ctx.rotate(90*Math.PI/180);
				if(toDraw) { ctx.fillStyle=color; }
				else { ctx.fillStyle="#00FF00"; color="#00FF00"; }

				drawF(step, color);
				ctx.restore();
        
				ctx.save();
				ctx.transform(0.5, 0, 0, 0.5, 250, 250);
if(toDraw) { ctx.fillStyle=color; }
else { ctx.fillStyle="#0000FF"; color="#0000FF"; }
				
				drawF(step, color);
				ctx.restore();
				
				ctx.save();
				ctx.transform(0.2, 0, 0, 0.25, 250, 250);
				ctx.scale(1,1);
				ctx.rotate(90*Math.PI/180);
        if(toDraw) { ctx.fillStyle=color; }
        else { ctx.fillStyle="#FFFF00"; color="#FFFF00"; }
        
				drawF(step, color);
				ctx.restore();
			} else {
				drawShape();
			}
		}
		function drawT() {
			ctx.beginPath();
			ctx.moveTo(0, 0);
			ctx.lineTo(500,0);
			ctx.lineTo(500,500);
			ctx.lineTo(300,500);
			ctx.lineTo(300,400);
			ctx.lineTo(150,400);
			ctx.lineTo(150,250);
			ctx.lineTo(0, 250);
			ctx.closePath();
			ctx.stroke();
		}

		function drawShape() {
			ctx.beginPath();
			ctx.moveTo(0,0);
			ctx.lineTo(500,0);
			ctx.lineTo(500,500);
			ctx.lineTo(300,500);
			ctx.lineTo(300,400);
			ctx.lineTo(150,400);
			ctx.lineTo(150,250);
			ctx.lineTo(0, 250);
			ctx.closePath();
			ctx.fill();
		}
	
	function showVal(newVal){
		draw(newVal);
	}
	</script>
</head>
	<body onload="draw();">
	   <canvas id="canvas" width="500" height="500"></canvas>
	</body>
	<input type="range" min="1" max="7" step="1" value="1"
	oninput="showVal(this.value)" onchange="showVal(this.value)">
</html>
```