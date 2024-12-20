---
uid: setcolor
---
[!INCLUDE [](graphics_header.md)]
# getcolor, setcolor
* getcolor returns the current drawing color
* setcolor sets the current drawing color

<br>

#### Declaration:
* int far getcolor(void);
* void far setcolor(int color);

<br>

### Remarks:
getcolor returns the current drawing color.<br><br>
setcolor sets the current drawing color to color, which can range from 0 to getmaxcolor.<br><br>
To select a drawing color with setcolor, you can pass either the color number or the [equivalent color name](COLORS.md).<br><br>
The drawing color is the value that pixels are set to when the program draws lines, etc.<br><br>
For example, in CGAC0 mode (palette number 0), the palette contains four colors (background, light green, light red, and yellow):<br>
* If getcolor returns 1, the current drawing color is light green.
* Either setcolor(3) or setcolor(CGA_YELLOW) selects yellow as the drawing color.

<br>

In CGAC3 mode, if getcolor returns 1, the current drawing color is cyan.<br><br>

##### Return Value:
* getcolor returns the current drawing color.
* setcolor does not return

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="getbkcolor.md">  getbkcolor   </a> <a href="getmaxcolor.md">  getmaxcolor  </a> <a href="getpalette.md">  getpalette   </a> <a href="graphresult.md">  graphresult  </a>
<a href="setallpalette.md">  setallpalette</a> <a href="setbkcolor.md">  setbkcolor   </a> <a href="setpalette.md">  setpalette   </a>
<br></div>

### Examples:
<div class="data"><a href="getcolor_example.md">  getcolor example</a> <a href="setcolor_example.md">  setcolor example</a>
</div>

<br>