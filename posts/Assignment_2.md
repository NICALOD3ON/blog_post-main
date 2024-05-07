---
title: A2 Chaotic! Documentation
published_at: 2023-03-3
snippet: My Assignment Two Documentation
disable_html_sanitization: true
---

### Introduction 
This first creative coding assignment requres us to explore the conventions of a 'Cute!' creative genre in p5. However, this first poses the question of: what makes a creative coding piece 'Cute'? This is something I hope to explore and iterate on upon further research and implementation of practice. I will also look to the works of artists such as Rafaël Rozendaal and course content to build my knowledge further.

### Reading Sianne Ngai - Zany, Cute, Interesting (Wark 2020)
The aesthetic idea of the 'zany' is a performative aesthetic that is 'hot and sweaty, anxious [and] excessive' (Ngai, 2020. 5). The author continues to define the aesthetic qualities of 'zany' as a feel for 'instability', or perhaps even an act of 'desperation' or 'stress'. The aesthetic itself is 'precarious' and 'forced', 'sexy' but not 'joyous' (Ngai, 7).

When I interpret this into my own words, I see the 'zany' easthetic as one that is barely containing itself. As if a 'digital body' were about to explode. I want to experiment creatively to represent what that looks like - what it feels like. How can I create texture? What kind of texture am I even looking for? These are the questions I have set for myself that I want to find the answer to. 

### Looking at Inspirational Artists & Works

####William Latham (Untitled) N.A
Below depicts one of the first inspirational pieces for me. Created by William Latham, a creative technologist, the work presents itself with jarring shape and textures. It seems course and sharp, as if it were a symbol for pressure, angst, and aggression. However, the negative space affectively resonates with me. It seems that behind the toughness, there is a lonesome void.

![Alt text](<../static/A2/art1.png>)

### Development & Iteration

```ps
function setup() {
  // Sets canvas to fill browser screen
      createCanvas(displayWidth, displayHeight);
}

function draw() {
  
  background(0);
  // Set stroke color to black
  stroke(255); 

  // Draw the initial radial fractal pattern
  drawRadialFractal(width / 2, height / 2, 150, 4);
}

function drawRadialFractal(x, y, length, depth) {
  if (depth === 1) {
    // Draws a short line
    // Generates random angles in variation
    let angle = random(TWO_PI); 
    let x2 = x + cos(angle) * length;
    let y2 = y + sin(angle) * length;
    //change later to x2
    line(x, y, x, y2);
  } else {
    // Recursion to draw six lines in a radial pattern
    for (let i = 0; i < 6; i++) {
      let angle = (i * PI) / 3;
      let x2 = x + cos(angle) * length;
      let y2 = y + sin(angle) * length;

      // Recursively draw each line
      // Determines the radius (size of fractal group)
      drawRadialFractal(x2, y2, length * 0.8, depth - 1);
    }
  }
}
```