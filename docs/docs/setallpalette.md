---
uid: setallpalette
---
[!INCLUDE [](graphics_header.md)]
# getdefaultpalette,<br>getpalette, and setallpalette
* getdefaultpalette returns the palette definition structure
* getpalette gets information about the current palette
* setallpalette changes all palette colors as specified

<br>

#### Declaration:
* struct palettetype *far getdefaultpalette(void);
* void far getpalette(struct palettetype far *palette);
* void far setallpalette(struct palettetype far *palette);

<br>

### Remarks:
* getdefaultpalette finds the [palettetype](palettetype.md) structure that contains the palette initialized by the driver during [initgraph](initgraph.md).

<br>

* getpalette fills the palettetype structure *palette with information about the current palette's size and colors.

<br>

* setallpalette sets the current palette to the values given in the [palettetype structure](palettetype.md) *palette. setallpalette can partially (or completely) change the colors in the EGA/VGA palette.

<div class="data">
 ┌────────────────────────────────────────┐
 │ NOTE: getpalette and setallpalette can │
 │       NOT be used with the IBM-8514    │
 │       driver. See <a href="setrgbpalette.md">setrgbpalette</a>.       │
 └────────────────────────────────────────┘
<br></div>

Valid colors depend on the current graphics driver and current graphics mode.<br><br>
Changes made to the palette appear onscreen immediately. Each time a palette color changes, all occurrences of that color change to the new color value.<br><br>

#####  Return Value:
* getdefault returns a pointer to the default palette set up by the current driver when that driver was initialized.
* getpalette and setallpalette do not return.

<br>

If invalid input is passed to setallpalette, graphresult returns -11 (grError), and the current palette remains unchanged.

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="getbkcolor.md">  getbkcolor    </a> <a href="getcolor.md">  getcolor      </a> <a href="getmaxcolor.md">  getmaxcolor   </a> <a href="getpalettesize.md">  getpalettesize</a>
<a href="graphresult.md">  graphresult   </a> <a href="setbkcolor.md">  setbkcolor    </a> <a href="setcolor.md">  setcolor      </a>
<br></div>

### Examples:
<div class="data"><a href="getdefaultpalette_example.md">  getdefaultpalette example</a> <a href="getpalette_example.md">  getpalette example       </a>
<a href="setallpalette_example.md">  setallpalette example    </a>
</div>

<br>