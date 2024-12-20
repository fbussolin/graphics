---
uid: linerel
---
[!INCLUDE [](graphics_header.md)]
# line, linerel, lineto
* line draws a line between two specified points
* linerel draws a line a relative distance from the current position (CP)
* lineto draws a line from the current position (CP) to (x,y)

<br>

#### Declaration:
* void far line(int x1, int y1, int x2, int y2);
* void far linerel(int dx, int dy);
* void far lineto(int x, int y);

<br>

### Remarks:
■ line draws a line from (x1, y1) to (x2, y2) using the current color, line style, and thickness. It does not update the current position (CP).<br><br>
■ linerel draws a line from the CP to a point that is a relative distance (dx, dy) from the CP, then advances the CP by (dx, dy).<br><br>
■ lineto draws a line from the CP to (x, y), then moves the CP to (x, y).<br><br>

#### Return Value:  None

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="getlinesettings.md">  getlinesettings</a> <a href="setcolor.md">  setcolor       </a> <a href="setlinestyle.md">  setlinestyle   </a> <a href="setvisualpage.md">  setvisualpage  </a>
<a href="setwritemode.md">  setwritemode   </a>
<br></div>

### Examples:
<div class="data"><a href="line_example.md">  line example   </a> <a href="linerel_example.md">  linerel example</a> <a href="lineto_example.md">  lineto example </a>
</div>

<br>