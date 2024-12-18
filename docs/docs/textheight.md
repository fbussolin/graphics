 ÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜ
 Ýtextheight, textwidthÞ         <GRAPHICS.H>
 ßßßßßßßßßßßßßßßßßßßßßßß
  þ textheight returns the height of a string in pixels
  þ textwidth returns the width of a string in pixels

 Declaration:
  þ int far textheight(char far *textstring);
  þ int far textwidth(char far *textstring);

 Remarks:
þ textheight takes the current font size and multiplication factor, and
determines the height of textstring in pixels.

þ textwidth takes the string length, current font size, and multiplication
factor, and determines the width of textstring in pixels.

These functions are useful for adjusting the spacing between lines,
computing viewport heights, sizing a title to make it fit on a graph or in a
box, etc..

For example, with the 8x8 bit-mapped font and a multiplication factor of 2
(set by settextstyle), the string "Borland C++" is 16 pixels high.

Instead of doing the computations manually, use textheight to compute the
height of strings, and use textwidth to compute their width.

When you use these functions, no source code modifications are required when
you select different fonts.

 Return Value:
textheight returns the text height in pixels. textwidth returns the text
width in pixels.

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

It works only with IBM PCs and compatibles equipped with supported graphics
display adapters.

 See Also:
  gettextsettings   outtext           outtextxy         settextstyle

 Examples:
  textheight example   textwidth example
