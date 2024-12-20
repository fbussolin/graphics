---
uid: fillpoly
---
[!INCLUDE [](graphics_header.md)]
# drawpoly, fillpoly
* drawpoly draws the outline of a polygon
* fillpoly draws and fills a polygon

<br>

#### Declaration:
* void far drawpoly(int numpoints, int far \*polypoints);
* void far fillpoly(int numpoints, int far \*polypoints);

<br>

### Remarks:  
drawpoly draws a polygon using the current line style and color.<br><br>
fillpoly draws the outline of a polygon using the current line style and color, then fills the polygon using the current fill pattern and fill color.<br>

<div class="data">
  Argument    │ What It Does
 ═════════════╪═════════════════════════════════════════════════
  numpoints   │ Specifies number of points
  *polypoints │ Points to a sequence of (numpoints x 2) integers
<br></div>

Each pair of integers gives the x and y coordinates of a point on the polygon.<br><br>
To draw a closed figure with N vertices, you must pass N+1 coordinates to drawpoly, where the Nth coordinate == the 0th coordinate.<br><br>

#### Return Value:  None

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="fill_patterns.md">  fill_patterns</a> <a href="floodfill.md">  floodfill    </a> <a href="graphresult.md">  graphresult  </a> <a href="setfillstyle.md">  setfillstyle </a>
<a href="setwritemode.md">  setwritemode </a>
<br></div>

### Examples:
<div class="data"><a href="drawpoly_example.md">  drawpoly example</a> <a href="fillpoly_example.md">  fillpoly example</a>
</div>

<br>