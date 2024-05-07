---
title: Week 5 
published_at: 2024-05-1
snippet: Investigating readings on Glitch Art
disable_html_sanitization: true
---

###Homework Task Week 7
1. Choose an example from weeks 4-6 you have implemented in your blog, and combine it with ideas from ascii camLinks to an external site., or Web Audio API samplesLinks to an external site. Post your process and result to your blog.

This is me exploring ascii cam:

![Alt text](<../static/A2/ascii.png>)

Something I find extremely aesthetically pleasing about this work is the affectiveness of the negative space balanced with the ascii detailing of each symbol. I truly find that this creative art embelishes the sense of structured pattern work, whilst also delving into contemporary art forms. Through this, we also see a strong example for media multiplices - presenting the power of creativity media and computational programs hold to generate such pieces.

```ps
<div id="ascii_div"></div>

<script type="module">

   // git camera stream, with options object   
   const stream = await navigator.mediaDevices.getUserMedia ({ 
      audio: false,
      video: true,
      facingMode: `user`,
   })

   // get video tracks
   const videoTracks = await stream.getVideoTracks ()
   console.log (`Using video device: ${ videoTracks[0].label }`)

   // make video html element
   const video = document.createElement (`video`)

   // assign stream to video source
   video.srcObject = stream
   await video.play ()

   // make canvas html element
   const cnv = document.createElement (`canvas`)

   // small size
   cnv.width  = 64

   // with aspect ratio from video html element
   cnv.height = cnv.width * video.videoHeight / video.videoWidth

   // grab the ascii div from DOM
   const div = document.getElementById (`ascii_div`)

   // set font to be monospace
   div.style.fontFamily = `monospace`

   // center aligned
   div.style.textAlign = `center`

   // get canvas context
   const ctx = cnv.getContext (`2d`)

   // string of characters from dark - bright
   const chars = "¶Ñ@%&∆∑∫#Wß¥$£√?!†§ºªµ¢çø∂æåπ*™≤≥≈∞~,.…_¬“‘˚`˙"

   // defining a function for animation
   const draw_frame = async () => {

      // tranformation save point
      ctx.save ()

      // flip horizontally
      ctx.scale (-1, 1)

      // draw image from video onto wrong side
      ctx.drawImage (video, -cnv.width, 0, cnv.width, cnv.height)

      // flip back
      ctx.restore ()

      // get pixel data
      const pixels = await ctx.getImageData (0, 0, cnv.width, cnv.height).data

      // start empty ascii string
      let ascii_img = ``


      for (let y = 0; y < cnv.height; y += 2) {
         for (let x = 0; x < cnv.width; x++) {

            // get pixel position
            const i = (y * cnv.width + x) * 4

            // get rgb values
            const r = pixels[i]
            const g = pixels[i + 1]
            const b = pixels[i + 2]

            // calculate brightness
            const br = (r * g * b / 16581376) ** 0.1

            // use brightness to select character
            const char_i = Math.floor (br * chars.length)

            // add character to ascii string
            ascii_img += chars[char_i]
         }

         // new line 
         ascii_img += `\n`
      }

      // add ascii string to innerText of div
      div.innerText = ascii_img

      // wait and then call next frame
      requestAnimationFrame (draw_frame)
   }

   // start recursive animation
   draw_frame ()
</script>
```
The code is sourced from the blog, not by me. I find this part of code very fascinating: I find the line of code beautiful in itself. The complexity of how computational devices and programs are able to create something from something as symbols is mind opening. It shows the potentiality for creativity across different mediums.

```ps
// string of characters from dark - bright
   const chars = "¶Ñ@%&∆∑∫#Wß¥$£√?!†§ºªµ¢çø∂æåπ*™≤≥≈∞~,.…_¬“‘˚`˙"
   ```

2. Why does combining ideas / libraries seem to make things more aesthetically chaotic?  Please refer to the principles of effective complexity in your answer.  Post your discussion to your blog.

Combining ideas aid in effectively create a piece that is aesthetically chaotic. Why? This is due to the affective phenomena of complexity and heterigeneity. This is the shared experience and emotions which evoke a distinct response. Affective complexity can fluctuate, combined, and fused. This can create a layer of emotions, feelings, and artisitc visuals. Throguh this, the aesthetic qualities of 'chaotic' are engaged. It feels loud, erratic, and messy - however, holds strong meaning.