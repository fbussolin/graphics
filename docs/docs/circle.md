---
uid: circle
---
[!INCLUDE [](../includes/graphics_header.md)]
# arc, circle, pieslice
* arc draws a circular arc
* circle draws a circle
* pieslice draws and fills a circular pie slice

#### Declaration:
* void far arc(int x, int y, int stangle, int endangle, int radius);
* void far circle(int x, int y, int radius);
* void far pieslice(int x, int y, int stangle, int endangle, int radius);

### Remarks:
arc draws a circular arc in the current drawing color.

circle draws a circle in the current drawing color.

pieslice draws a pie slice in the current drawing color, then fills it using the current fill pattern and fill color.

<div class="data">
  Argument │ What It Is/Does
 ══════════╪════════════════════════════════════════════
  (x,y)    │ Center point of arc, circlew, or pie slice
  stangle  │ Start angle in degrees
  endangle │ End angle in degrees
  radius   │ Radius of arc, circle, and pieslice
</div>

The arc or slice travels from stangle to endangle.

If stangle = 0 and endangle = 360, the call to arc draws a complete circle.

If your circles are not perfectly round, use setaspectratio to adjust the aspect ratio.

###### Angle for arc, circle, and pieslice (counter-clockwise)

<div class="data">
             90  
          degrees  
             ║  
             ║  
   180 ══════╬══════  0 degrees,
 degrees     ║      360 degrees
             ║
            270
          degrees
</div>

The linestyle parameter does not affect arcs, circles, ellipses, or pie slices. Only the thickness parameter is used.

If you're using a CGA in high resolution mode or a monochrome graphics adapter, examples in this Help system that show how to use graphics functions might not produce the expected results.

If your system runs on a CGA or monochrome adapter, pass 1 to those functions that alter the fill or drawing color (don't pass one of the symbolic color constants defined in GRAPHICS.H).

<br>

#### Return Value: None

<br>

### Portability:
<div class="data">
 ╔ DOS ╤ UNIX ╤ Windows ╤ ANSI C ╤ C++ Only ╗
 ║ Yes │      │         │        │          ║
 ╚═════╧══════╧═════════╧════════╧══════════╝
</div>

### See Also:
<div class="data">
<a href="ellipse.md">  ellipse        </a> <a href="fill_patterns.md">  fill_patterns  </a> <a href="fillellipse.md">  fillellipse    </a> <a href="getarccoords.md">  getarccoords   </a>
<a href="getaspectratio.md">  getaspectratio </a> <a href="graphresult.md">  graphresult    </a> <a href="setfillpattern.md">  setfillpattern </a> <a href="setfillstyle.md">  setfillstyle   </a>
<a href="setgraphbufsize.md">  setgraphbufsize</a>
</div>

### Examples:
<div class="data">
<a href="arc_example.md">  arc example     </a> <a href="circle_example.md">  circle example  </a> <a href="pieslice_example.md">  pieslice example</a>
</div>