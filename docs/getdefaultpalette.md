 ÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜ
 Ýgetdefaultpalette,           Þ
 Ýgetpalette, and setallpaletteÞ <GRAPHICS.H>
 ßßßßßßßßßßßßßßßßßßßßßßßßßßßßßßß
  þ getdefaultpalette returns the palette definition structure
  þ getpalette gets information about the current palette
  þ setallpalette changes all palette colors as specified

 Declaration:
  þ struct palettetype *far getdefaultpalette(void);
  þ void far getpalette(struct palettetype far *palette);
  þ void far setallpalette(struct palettetype far *palette);

 Remarks:
þ getdefaultpalette finds the palettetype structure that contains the
palette initialized by the driver during initgraph.

þ getpalette fills the palettetype structure *palette with information about
the current palette's size and colors.

þ setallpalette sets the current palette to the values given in the
palettetype structure *palette. setallpalette can partially (or completely)
change the colors in the EGA/VGA palette.

 ÚÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ¿
 ³ NOTE: getpalette and setallpalette can ³
 ³       NOT be used with the IBM-8514    ³
 ³       driver. See setrgbpalette.       ³
 ÀÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÙ

Valid colors depend on the current graphics driver and current graphics
mode.

Changes made to the palette appear onscreen immediately. Each time a palette
color changes, all occurrences of that color change to the new color value.

 Return Value:
  þ getdefault returns a pointer to the
    default palette set up by the current
    driver when that driver was initialized.
  þ getpalette and setallpalette do not
    return.

If invalid input is passed to setallpalette, graphresult returns -11
(grError), and the current palette remains unchanged.

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  getbkcolor       getcolor         getmaxcolor      getpalettesize
  graphresult      setbkcolor       setcolor

 Examples:
  getdefaultpalette example   getpalette example
  setallpalette example
