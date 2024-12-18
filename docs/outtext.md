 ÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜ
 Ýouttext, outtextxyÞ            <GRAPHICS.H>
 ßßßßßßßßßßßßßßßßßßßß
  þ outtext displays a string in the viewport (graphics mode)
  þ outtextxy displays a string at the specified location (graphics mode)

 Declaration:
  þ void far outtext(char far *textstring);
  þ void far outtextxy(int x, int y, char far *textstring);

 Remarks:
outtext and outtextxy display a text string, using the current justification
settings and the current font, direction, and size.
  þ outtext outputs textstring at the current position (CP)
  þ outtextxy displays textstring in the viewport at the position (x, y)

To maintain code compatibility when using several fonts, use textwidth and
textheight to determine the dimensions of the string.

If a string is printed with the default font using outtext or outtextxy, any
part of the string that extends outside the current viewport is truncated.

With outtext, if the horizontal text justification is LEFT_TEXT and the text
direction is HORIZ_DIR, the CP's x-coordinate is advanced by
textwidth(textstring).

Otherwise, the CP remains unchanged.

outtext and outtextxy are for use in graphics mode; they will not work in
text mode.

 Return Value: None

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  gettextsettings   settextjustify

 Examples:
  outtext example     outtextxy example
