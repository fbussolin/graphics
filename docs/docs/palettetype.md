---
uid: palettetype
---
[!INCLUDE [](graphics_header.md)]
###### &nbsp;palettetype&nbsp;

Contains palette information for the current graphics driver when calling [getpalette](getpalette.md), [setpalette](setpalette.md), and [setallpalette](setallpalette.md).<br>

<div class="data">
  struct palettetype {
    unsigned char  size;
    signed   char  colors[<a href="MAXCOLORS.md">MAXCOLORS</a>+1];
  };
</div>
<div class="data">
  Element│ What It Is/Does
 ════════╪═══════════════════════════════════════════════════════════════════
  size   │ Gives the number of colors in the palette for the current
         │ graphics driver in the current mode.
  colors │ An array of size bytes containing the actual raw color numbers
         │ for each entry in the palette. If an element of colors is
         │ -1, the palette color for that entry is not changed.
</div>

<br>