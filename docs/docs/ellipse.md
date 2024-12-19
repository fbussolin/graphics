---
uid: ellipse
---
[!INCLUDE [](../includes/graphics_header.md)]
# ellipse, fillellipse, sector
* ellipse draws an elliptical arc
* fillellipse draws and fills an ellipse
* sector draws and fills an elliptical pie slice

<br>

#### Declaration:
* void far ellipse(int x, int y, int stangle, int endangle,  
&nbsp;&nbsp;int xradius, int yradius);
* void far fillellipse(int x, int y,  
&nbsp;&nbsp;int xradius, int yradius);
* void far sector(int x, int y, int stangle, int endangle,  
&nbsp;&nbsp;int xradius, int yradius);

<br>

### Remarks:
ellipse draws an elliptical arc in the current drawing color.<br><br>
fillellipse draws an ellipse, then fills the ellipse with the current fill color and fill pattern.<br><br>
sector draws and fills an elliptical pie slice in the current drawing color, then fills it using the pattern and color defined by [setfillstyle](setfillstyle.md) or [setfillpattern](setfillpattern.md).<br>

<div class="data">
  Argument │ What It Is
 ══════════╪═══════════════════
  (x,y)    │ Center of ellipse
  xradius  │ Horizontal axis
  yradius  │ Vertical axis
  stangle  │ Starting angle
  endangle │ Ending angle
<br></div>

The ellipse or sector travels from stangle to endangle.<br><br>
If stangle = 0 and endangle = 360, the call to ellipse draws a complete ellipse.<br><br>

###### Angle for ellipse, fillellipse, and sector (counter-clockwise)
<div class="data">
             90
          degrees
             ║
             ║
   180 ══════╬══════  0 degrees,
 degrees     ║      360 degrees
             ║
           270 degrees
<br></div>

The linestyle parameter does not affect arcs, circles, ellipses, or pieslices. Only the thickness parameter is used.<br><br>

#### Return Value:  None

<br>

If an error occurs while the elliptical pie slice is filling, [graphresult](graphresult.md) returns -6 (grNoScanMem).

[!INCLUDE [](../includes/portability.md)]

### See Also:
<div class="data"><a href="arc.md">  arc           </a> <a href="circle.md">  circle        </a> <a href="getaspectratio.md">  getaspectratio</a> <a href="pieslice.md">  pieslice      </a>
<a href="setaspectratio.md">  setaspectratio</a>
<br></div>

### Example:
<div class="data"><a href="ellipse_example.md">  ellipse example    </a> <a href="fillellipse_example.md">  fillellipse example</a> <a href="sector_example.md">  sector example     </a>
</div>

<br>