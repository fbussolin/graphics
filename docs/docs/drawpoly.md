---
uid: drawpoly
---
[!INCLUDE [](../includes/graphics_header.md)]
# drawpoly, fillpoly

* drawpoly draws the outline of a polygon
* fillpoly draws and fills a polygon

#### Declaration:
* void far drawpoly(int numpoints, int far *polypoints);
* void far fillpoly(int numpoints, int far *polypoints);

### Remarks:  
drawpoly draws a polygon using the current line style and color.

fillpoly draws the outline of a polygon using the current line style and color, then fills the polygon using the current fill pattern and fill color.

<div class="data">
  Argument    │ What It Does
 ═════════════╪═════════════════════════════════════════════════
  numpoints   │ Specifies number of points
  *polypoints │ Points to a sequence of (numpoints x 2) integers
</div>

Each pair of integers gives the x and y coordinates of a point on the polygon.

To draw a closed figure with N vertices, you must pass N+1 coordinates to drawpoly, where the Nth coordinate == the 0th coordinate.

#### Return Value:  None

<br>

### Portability:
<div class="data">
 ╔ DOS ╤ UNIX ╤ Windows ╤ ANSI C ╤ C++ Only ╗
 ║ Yes │      │         │        │          ║
 ╚═════╧══════╧═════════╧════════╧══════════╝
</div>

### See Also:
<div class="data">
<a href="fill_patterns.md">  fill_patterns</a> <a href="floodfill.md">  floodfill    </a> <a href="graphresult.md">  graphresult  </a> <a href="setfillstyle.md">  setfillstyle </a>
<a href="setwritemode.md">  setwritemode </a>
</div>

### Examples:
<div class="data">
<a href="drawpoly_example.md">  drawpoly example</a> <a href="fillpoly_example.md">  fillpoly example</a>
</div>