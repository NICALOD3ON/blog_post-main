---
title: A2 Chaotic! Documentation
published_at: 2024-05-5
snippet: My Assignment Two Documentation
disable_html_sanitization: true
---

### Introduction 
This first creative coding assignment requres us to explore the conventions of a 'Cute!' creative genre in p5. However, this first poses the question of: what makes a creative coding piece 'Cute'? This is something I hope to explore and iterate on upon further research and implementation of practice. I will also look to the works of artists such as Rafaël Rozendaal and course content to build my knowledge further.

### Reading Sianne Ngai - Zany, Cute, Interesting (Wark 2020)
The aesthetic idea of the 'zany' is a performative aesthetic that is 'hot and sweaty, anxious [and] excessive' (Ngai, 2020. 5). The author continues to define the aesthetic qualities of 'zany' as a feel for 'instability', or perhaps even an act of 'desperation' or 'stress'. The aesthetic itself is 'precarious' and 'forced', 'sexy' but not 'joyous' (Ngai, 7).

When I interpret this into my own words, I see the 'zany' easthetic as one that is barely containing itself. As if a 'digital body' were about to explode. I want to experiment creatively to represent what that looks like - what it feels like. How can I create texture? What kind of texture am I even looking for? These are the questions I have set for myself that I want to find the answer to. 

### Looking at Inspirational Artists & Works

####William Latham (Untitled) N.D
Below depicts one of the first inspirational pieces for me. Created by William Latham, a creative technologist, the work presents itself with jarring shape and textures. It seems course and sharp, as if it were a symbol for pressure, angst, and aggression. However, the negative space affectively resonates with me. It seems that behind the toughness, there is a lonesome void.

![William Latham Artwork](<../static/A2/art1.png>)

####Kerry Mitchell, Clinamen (2017)
In this second inspirational work, I admire the artists colour palette of black and white and the pattern it creates. if we look closer, we are also able to see a subtle linear grid - providing the piece with stucture and strength. It is so unified yet so sparratic. It feels as if it embodies the sound of white noise so beautifully. When looking at this visual, it feels very ambient in some way. It feels as if there was a 'melodic disharmony' that would sound unsettling yet grew to become a sense of comfort. Mitchell's work seems like it could be representative of our world - a new life where our world is shaped by the anthropocene. This new, futuristic world comes at the cost of our earth, yet we many privelege the ability to 'turn a blind eye' and live comfortably admist the reality. This work opens up many interpretations and is something I hope to carry out in future design works throughout my practice.

![Kerry Mitchel, Clinamen (2017)](<../static/A2/art2.png>)

####Desmond Paul Henry, Archives (1965)

One of the many elements I value most in this piece is the power negative space holds within the background as it creates a deep void. However, this void doesn't seem 'fearful' but more so 'beautiful' as it compliments the white web-like structure of the piece. The composition as a whole balances together, affectively presenting organic structures and movement although it is still. When analysing this piece closer, we are able to identify a large variation of small linear fractals side by side to form this structure. It seems so 'chaotic' yet 'put together', this is something I truly find fascinating about Henry's work.

![Desmond Paul Henry, Archives (1965)](<../static/A2/art3.png>)

####Mathieu St-Pierre, Series: Dorm 2 (2012)

This glitch artist utilises the power the greyscale specturm holds in glitch art. It easily manipulates the evocative feeling and emotion of the piece from something that once had colour and meaning, to something 'gloomy' and almost 'pleading'. Whilst I do not intend to play with illustration, I hope to incorporate St-Pierres horisontal glitch effect. I find inspiration in this element of St-Pierre's work as it aims to distort but not take away meaning or intention of the work.

![Mathieu St-Pierre, Series: Dorm 2 (2012)](<../static/A2/art4.png>)

### Development & Iteration

First, I added 'createCanvas(displayWidth, displayHeight);' to the setup function of my sketch. This allows the canvas to fit the screen of the browser. This means the sketch will always fit the size of the browser if its reshaped or full screen. This is important as it affctivly engages audiences focus as well as their ability to resonate with the work and its performance.

```ps
function setup() {
  // Sets canvas to fill browser screen
      createCanvas(displayWidth, displayHeight);
}
```
Following this, I set the background and stroke colour. I want to set the background to black so i add 'background(0)' which is the lowest value. To make the stroke (elements on top of the background) white, I add 'stroke(255)' which is the highest value. Therefore, the result so far is a black background and the white strokes will appear once I draw elements onto the canvas. 

![Alt text](<../static/A2/pro1.png>)

```ps
function draw() {
  
  background(0);
  // Set stroke color to white and background black
  stroke(255); 
```
From this point, I must first set up a function to be able to draw the function. For this project, I want to take inspiration from the artists works I had researched and documented on my blog. Therefore, I want to mainly draw to the element of 'fractals' - a reoccuring element that unifies the composition whilst also evoking a sense of performed aethetic chaos.

When considering the possible design pathways, I found through inpirational artistic research that I deeply appreciated smaller linear details within works, for example in Desmon Paul Henry's Archive works. 

The function 'drawRadialFractal' is designed to draw a fractal pattern. This unique pattern will consist of multiple lines that branch out from a central point on x and y. This will form in a radial pattern.

```ps
function drawRadialFractal(x, y, length, depth) {}
```
'if (depth === 1){' checks that the depth of recursion is 1. This should be the base case where the fractal branches will draw simple short lines.

```ps
  if (depth === 1) {
```

The next line of code, I want to create random angles raidally. To do this, creating a 'let' variable in relation to 'angle' equal 'random(TWO_PI)' will generate lines on a random angle around a circle. The 'random' part of the code returns a floating point number between 'inclusive' and 'exclusive' values (0 and 1).

```ps
    let angle = random(TWO_PI); 
```

The two following lines calculate the endpoint of eah line. I want them to be quite short first, so I want to set them for 'x2' and 'y2'. They both use trigonomic functions of 'cos' and 'sin' - this is something I really struggled to figure out and understand. Due to this personal complication, I accessed the p5 references for help for 'constants' and then looking into 'TWO_PI' an how it works. Here: https://p5js.org/reference/#/p5/TWO_PI

```ps
    let x2 = x + cos(angle) * length;
    let y2 = y + sin(angle) * length;
```

The next line of code 'line(x, y, x, y2);' Draws the line segment from the initial point to the indicated endpoint. This should create a variation of vertical line segments (lines that go from up to down or upright).

```ps
    line(x, y, x, y2);
```
The next line carries out the boolean constant from 'if (depth)'. The 'else' block means that when depth is greater than 1, the fractal will branch out further. Sort of similar to like branches of a tree. This alone is interestic because although creative coding it digitised, it shares and is inspired by organic elements in our realistic world.

```ps
  } else {
```
The next line means there is now a loop within the function. This means the 'fragments' will iterate six times to create six branches. I went with six as the numerology meaning means 'charm, destiny, and empathy.' Here: https://www.ganeshaspeaks.com/numerology/numbers/6-six/#google_vignette 

To me, this is intentionally relevant as it is a depiction of 'chaos' in my own words/interpretation. The aesthetic of 'chaos' is charming in its own way due to its performed yet structured 'messiness'. In some ways, the feeling of 'chaos' seems 'destined', like we are all meants to experience this as it is a phenomenon that comes across for all of us as a learning obstacle. Then 'empathy' - through everything, amongst all the chaos in our lives and moments off blur, we must always empathise for ourselves to also then empathise for others around us. This is what makes us human. 

```ps
    for (let i = 0; i < 6; i++) {
```
The next line of code determines the angle of PI. Through this loop, it guarantees an even distribution between each point around the central point of the x and y axis.

```ps
      let angle = (i * PI) / 3;
```
Creating more let variables for x2 and xy once again, just set the start and end point for each recursive line.

```ps
      let x2 = x + cos(angle) * length;
      let y2 = y + sin(angle) * length;
```
The draw function on the next line 'drawRadialFractal()' draws the fractals recusively. The length is reduced by 20% due to the block '(length * 0.8')' and decreases the depth by 1 due to 'depth - 1'. This was done or stylistic purposes, and was achievable through the p5 resource help page.

```ps
      drawRadialFractal(x2, y2, length * 0.8, depth - 1);
```
Now that our radial fractal function is set up, I can now 'draw' the function onto the canvas. To do this, I set the width and height to be of the centre point on the canvas. (Horizontal and Vetical points).

I want to play with the length of the line fragments, as I am not sure what I want for it. I start of with '100'.

![Alt text](<../static/A2/pro2.png>)

```ps
  drawRadialFractal(width / 2, height / 2, 100, 4);
}
```

I see that the fragmented lines form almost a circle, but more hexagonal shape in the centre of the composition. However, I feel as if it is so small. I do want to show the power nexative space has within works, but this just feels more empty and it is not what I intend.

I then try again and replace the '100' with the value '150' to determine how much bigger the visuals appear on the canvas.

![Alt text](<../static/A2/pro3.png>)

```ps
  drawRadialFractal(width / 2, height / 2, 150, 4);
}
```
However, I still feel like it is quite small. From this point, i wonder if anything is changing at all. Must I change it? Will anything feel different if I do? I want to text this out, so I replace '150' with '200'.

![Alt text](<../static/A2/pro4.png>)

```ps
  drawRadialFractal(width / 2, height / 2, 200, 4);
}
```

This outcome is definitely headed more to what I was envisioning. It still carries out the power of the negative space, whilst also bringing attention to the work itself. 

The outcome I am quite happy with, as it seems to create a vertically linear glitch-like effect. However, I feel like it is still quite empty - like it is missing something. From this point, I think it is necessary to call back to my stylistic inspirations from artists. 

![Alt text](<../static/A2/pro5.png>)

When I look back at the elements I adored about William Latham's work, I was vey fond of the 'erratic' shape of the subject in this piece as it felt like it radiated a sense of power, tension, and self doubt within the 'lonesome void'. Now, I pose the question for myself: How will I incorporate this aspect into my work? How can I develop this idea into something that creates movement and represents the 'course' texture of what I see? This is something I find very difficult to wrap my head around as I feel as if I cannot make it there, yet I so desperately want to.

I look back at my lines of code, and I know it will have something to do with the angles I had created for the draw function.

```ps
let angle = random(TWO_PI); 
    let x2 = x + cos(angle) * length;
    let y2 = y + sin(angle) * length;
    line(x, y, x, y2);
```

I know that the answer lies in these four lines, but I really am not sure of what I can do to them to make this desired change. When I re-evaluate why I had written these lines of code, I know that the first line is only defining the variable. The second and third line defines variables x2 and y2, so it doesn't actually create the 'foundation' of its function. Determining this, I know its the fourth line and I see what I have to change.

![Alt text](<../static/A2/pro6.png>)

```ps
line(x, y, x2, y2);
```
It now feels more erratic and chaotic. Though when looking at the movements, it feels too fast and its distracting from my intention. To experiment further, I changed the length in this line from 1.8 to 1 to see what would happen as I am unsure. In doing this, I found that it upscaled the sketch as well as emphasised the central points from where the fractals start from. I actually come to appreciate the visual, as it reminds me of the stars you'd see at night and think of them as 'hope'. However, if we were to look closer at these stars, they radiate a strong energy - yet it is still so beautiful. So is the aesthetic of chaos.

```ps
drawRadialFractal(x2, y2, length * 1, depth - 1);
```

![Alt text](<../static/A2/pro7.png>)

Now that I have achieved this, I have came to the feeling again that it is still missing something. What is it missing? I feel as if I had added exactly what I wanted but it is calling for something else.

I had to sit with this for a moment. Then, I thought back to the intention of this project - chaos. Then I posed the question; "How do I interpret the story of chaos? How does it feel? What thought evokes this feeling?". I then thought back to what story the fractals told for me. The way I saw them as stars of hope, and how behind it, is a burning energy that is chaotic yet beautiful. How can I make this thought subconciously resonate with someone else?

From this point of ideation, I now want to experiment with the use of text and its affective power. Thinking back to my first few weeks of my Creative Coding Class, I had revisited modules that explained how to add text both in the console and on the canvas. I then added in my draw function:

```ps
// Align text to center
  textAlign(CENTER, CENTER); 
  // Set text size
  textSize(48); 
  // Set text fill color to white
  fill(255); 
  // Set font to Arial
  textFont('Arial'); 
```
This section of code sets up the foundation for what I want my text to look like. I set the position, text sizes, the colour of text, and the font of my text to what I wanted. I figured the text would have to be bold to stand out and act as a focal point within the composition, to then convey the message or 'point of thought' that I had intended strongly amongst the movements in the background. Therefore, I had chosen Arial as it is easy to read. The text would read: "can i hold onto hope?".

**Why this?** I feel that this message positions audience with a strong, commonly self reflected question. In times where we feel like we are stuck in a deep void surrounded by chaotic and messy thoughts, we often look for a 'hope' to keep us grounded. Then, after hoping and hoping, at some point many of us start to feel hopeless. This is humanity and its real. Through this message, I hope to emotionally resonate with others as I do with this work.

```ps
 text("can I hold onto hope?")
```
![Alt text](<../static/A2/pro8.png>)

Whilst I am happy with the turnout, I feel as if I can add more to this composition. I want to really represent just how 'unstable' this thought can be. Often, this question is paired with the feeling of 'doubt'... so what does this feel like? For me, it feels shaky. It feels as if I am about to crumble and I am pleading for an answer - an answer that will uplift me. Therefore, I want to create a glitch in the text or replicate an intense or semi-intense shake. To do this, I will look into the 'noise' function on p5 resources. 

![Alt text](<../static/A2/pro9.png>)

This is what I had come across on the p5 resource page (here: https://p5js.org/reference/#/p5/noise). Therefore, I will attempt to intergrate this into my work. I want the movement to be fast but not too fast, as if there was still composure but almost breaking it.

```ps
  let noiseX = noise(frameCount * 0.01) * 20 - 10; // Noise for x position
  let noiseY = noise(frameCount * 0.01 + 1000) * 20 - 10; // Noise for y position
  text("can I hold onto hope?", width / 2 + noiseX, height / 2 + noiseY);
```

I set variables for the noise coordinates as 'noiseX' and 'noiseY' as I already have variables 'x' and 'y' used for the fractals. The value 0.01 determines how fast the change is between noiseX and noiseY. However, I felt that the movement of the text was slower than what I had wanted, so I changed the value 0.01 to 0.1 to increase the intensity of movement.

```ps
let noiseX = noise(frameCount * 0.1) * 20 - 10; // Noise for x position
  let noiseY = noise(frameCount * 0.1 + 1000) * 20 - 10; // Noise for y position
```

However, now I felt as if itwas a bit too fast - not maintaining the little composure I had hoped for. So perhaps I will change the value 0.1 t0 0.05. After doing this, I thought the text would have moved slower, but it moved even faster than before. I now will change it. As I went to make these changes, I realsed that I had entered the value 0.5 instead of 0.05 which explains the unexpectancy. I continued to experiment with different values regardless, and have set noiseX to 0.05 and noiseY to 0.2. This created a composed yet subtle erratic movement in the text.

This is the link to my final sketch: https://editor.p5js.org/NICALOD3ON/full/58ts48b9h

Thank you for taking the time to read my blog!

