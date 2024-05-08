---
title: Week 5 
published_at: 2024-04-1
snippet: Investigating readings on Glitch Art
disable_html_sanitization: true
---

#### The Phenomenology of Glitch Art

#### Glitch Feminism: Glitch is a Skin

```ps
<canvas id="glitch_self_portrait"></canvas>

<script type="module">

    <!-- getting canvas element -->
   const cnv = document.getElementById (`glitch_self_portrait`)
    //    sizing to be good size
   cnv.width = cnv.parentNode.scrollWidth
   cnv.height = cnv.width * 9 / 16
    //    setting background colour
   cnv.style.backgroundColor = `deeppink`

    // giving canvas context
   const ctx = cnv.getContext (`2d`)

    // instantiated variable for image data
   let img_data

    // defining a fuction that draws an image to the canvas
   const draw = i => ctx.drawImage (i, 0, 0, cnv.width, cnv.height)

    // creating a new image element
   const img = new Image ()
   img.onload = () => {

      // resizing the image
      // to be same aspect ratio as image
      cnv.height = cnv.width * (img.height / img.width)
      //   drawing the image
      draw (img)
      //   stores image data as a string
      img_data = cnv.toDataURL ("image/jpeg")
      //   calls a glitch function
      add_glitch ()
   }
    //    give file pathto image element
   img.src = `/A1/water.jpg`

// adds a function, generating a random value and chops off the decimal points. returning a random integer between 0 and max.
   const rand_int = max => Math.floor (Math.random () * max)

// define a recursive function
   const glitchify = (data, chunk_max, repeats) => {
    // random mulyiple of 4 between 0 and max
      const chunk_size = rand_int (chunk_max / 4) * 4
    //   random position in the data between 24 - chunk size
      const i = rand_int (data.length - 24 - chunk_size) + 24
    //   grabbing all data before random position
      const front = data.slice (0, i)
    //   leaving gap the size of chunk
    // leaving out a chunk
      const back = data.slice (i + chunk_size, data.length)
      const result = front + back
    //   ternary operator - 
      return repeats == 0 ? result : glitchify (result, chunk_max, repeats - 1)
   }
// creates enpty array for glitches
   const glitch_arr = []

// makes a new glitch image
   const add_glitch = () => {

      const i = new Image ()
      i.onload = () => {
         glitch_arr.push (i)
         if (glitch_arr.length < 12) add_glitch ()
         else draw_frame ()
      }
      i.src = glitchify (img_data, 96, 6)
   }

   let is_glitching = false
   let glitch_i = 0

   const draw_frame = () => {

    // check to see if glitch is happening or not
    // if yes, draw glitched image from the array
      if (is_glitching) draw (glitch_arr[glitch_i])
    //   otherwise draw regular image
      else draw (img)


      const prob = is_glitching ? 0.05 : 0.02
      if (Math.random () < prob) {
         glitch_i = rand_int (glitch_arr.length)
         is_glitching = !is_glitching
      }

// call next animation frame
      requestAnimationFrame (draw_frame)
   }

</script>

```ps
<canvas id="glitch_self_portrait"></canvas>

<script type="module">

    <!-- getting canvas element -->
   const cnv = document.getElementById (`glitch_self_portrait`)
   <!-- sizing to be good size  -->
   cnv.width = cnv.parentNode.scrollWidth
   cnv.height = cnv.width * 9 / 16
   cnv.style.backgroundColor = `deeppink`

   const ctx = cnv.getContext (`2d`)

   let img_data

   const draw = i => ctx.drawImage (i, 0, 0, cnv.width, cnv.height)

   const img = new Image ()
   img.onload = () => {
      cnv.height = cnv.width * (img.height / img.width)
      draw (img)
      img_data = cnv.toDataURL ("image/jpeg")
      add_glitch ()
   }
   img.src = `/static/water.jpg`

   const rand_int = max => Math.floor (Math.random () * max)

   const glitchify = (data, chunk_max, repeats) => {
      const chunk_size = rand_int (chunk_max / 4) * 4
      const i = rand_int (data.length - 24 - chunk_size) + 24
      const front = data.slice (0, i)
      const back = data.slice (i + chunk_size, data.length)
      const result = front + back
      return repeats == 0 ? result : glitchify (result, chunk_max, repeats - 1)
   }

   const glitch_arr = []

   const add_glitch = () => {
      const i = new Image ()
      i.onload = () => {
         glitch_arr.push (i)
         if (glitch_arr.length < 12) add_glitch ()
         else draw_frame ()
      }
      i.src = glitchify (img_data, 96, 6)
   }

   let is_glitching = false
   let glitch_i = 0

   const draw_frame = () => {
      if (is_glitching) draw (glitch_arr[glitch_i])
      else draw (img)

      const prob = is_glitching ? 0.05 : 0.02
      if (Math.random () < prob) {
         glitch_i = rand_int (glitch_arr.length)
         is_glitching = !is_glitching
      }

      requestAnimationFrame (draw_frame)
   }

</script>
```