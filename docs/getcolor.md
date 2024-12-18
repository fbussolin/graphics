 ÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜ
 Ýgetcolor, setcolorÞ            <GRAPHICS.H>
 ßßßßßßßßßßßßßßßßßßßß
  þ getcolor returns the current drawing color
  þ setcolor sets the current drawing color

 Declaration:
  þ int far getcolor(void);
  þ void far setcolor(int color);

 Remarks:
getcolor returns the current drawing color.

setcolor sets the current drawing color to color, which can range from 0 to
getmaxcolor.

To select a drawing color with setcolor, you can pass either the color
number or the equivalent color name.

The drawing color is the value that pixels are set to when the program draws
lines, etc.

For example, in CGAC0 mode (palette number 0), the palette contains four
colors (background, light green, light red, and yellow):
  þ If getcolor returns 1, the current drawing
    color is light green.
  þ Either setcolor(3) or setcolor(CGA_YELLOW)
    selects yellow as the drawing color.

In CGAC3 mode, if getcolor returns 1, the current drawing color is cyan.

 Return Value:
  þ getcolor returns the current drawing color.
  þ setcolor does not return

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  getbkcolor      getmaxcolor     getpalette      graphresult
  setallpalette   setbkcolor      setpalette

 Examples:
  getcolor example   setcolor example
