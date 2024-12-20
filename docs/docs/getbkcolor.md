---
uid: getbkcolor
---
[!INCLUDE [](graphics_header.md)]
# getbkcolor, setbkcolor
* getbkcolor returns the current background color
* setbkcolor sets the current background color using the palette

<br>

#### Declaration:
* int far getbkcolor(void);
* void far setbkcolor(int color);

<br>

### Remarks:
getbkcolor returns the current background color.<br><br>
setbkcolor sets the background to the color specified by color.<br><br>

###### color
color is either a number or [symbolic name](COLORS.md) specifying the color to set.<br><br>
For example, if you want to set the background color to blue, you can call<br><br>
&nbsp;&nbsp;setbkcolor(BLUE) /* or */ setbkcolor(1)<br><br>
On CGA and EGA systems, setbkcolor changes the background color by changing the first entry in the palette.<br><br>
On an EGA or a VGA, if you call setpalette or setallpalette to change the palette colors, the defined symbolic constants might not give the correct color.<br><br>
This is because the color parameter to setbkcolor indicates the entry number in the current palette, rather than a specific color. (Except 0, which always sets the background color to black).<br><br>

##### Return Value:  None
* getbkcolor returns the current background color.
* setbkcolor does not return.

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="getcolor.md">  getcolor     </a> <a href="getmaxcolor.md">  getmaxcolor  </a> <a href="getpalette.md">  getpalette   </a> <a href="setallpalette.md">  setallpalette</a>
<a href="setcolor.md">  setcolor     </a> <a href="setpalette.md">  setpalette   </a>
<br></div>

### Examples:
<div class="data"><a href="getbkcolor_example.md">  getbkcolor example</a> <a href="setbkcolor_example.md">  setbkcolor example</a>
</div>

<br>