
  palettetype                    <GRAPHICS.H>
 ßßßßßßßßßßßßß
Contains palette information for the current graphics driver when calling
getpalette, setpalette, and setallpalette.

  struct palettetype {
    unsigned char  size;
    signed   char  colors[MAXCOLORS+1];
  };

  Element³ What It Is/Does
 ÍÍÍÍÍÍÍÍØÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍ
  size   ³ Gives the number of colors in the palette for the current
         ³ graphics driver in the current mode.
  colors ³ An array of size bytes containing the actual raw color numbers
         ³ for each entry in the palette. If an element of colors is
         ³ -1, the palette color for that entry is not changed.
