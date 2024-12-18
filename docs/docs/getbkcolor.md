 ÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜ
 Ýgetbkcolor, setbkcolorÞ        <GRAPHICS.H>
 ßßßßßßßßßßßßßßßßßßßßßßßß
  þ getbkcolor returns the current background color
  þ setbkcolor sets the current background color using the palette

 Declaration:
  þ int far getbkcolor(void);
  þ void far setbkcolor(int color);

 Remarks:
getbkcolor returns the current background color.

setbkcolor sets the background to the color specified by color.

 color
 ßßßßß
color is either a number or symbolic name specifying the color to set.

For example, if you want to set the background color to blue, you can call

  setbkcolor(BLUE) /* or */ setbkcolor(1)

On CGA and EGA systems, setbkcolor changes the background color by changing
the first entry in the palette.

On an EGA or a VGA, if you call setpalette or setallpalette to change the
palette colors, the defined symbolic constants might not give the correct
color.

This is because the color parameter to setbkcolor indicates the entry number
in the current palette, rather than a specific color. (Except 0, which
always sets the background color to black).

 Return Value:
  þ getbkcolor returns the current background
    color.
  þ setbkcolor does not return.

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  getcolor        getmaxcolor     getpalette      setallpalette
  setcolor        setpalette

 Examples:
  getbkcolor example   setbkcolor example
