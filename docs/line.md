 ÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜ
 Ýline, linerel, linetoÞ         <GRAPHICS.H>
 ßßßßßßßßßßßßßßßßßßßßßßß
  þ line draws a line between two specified points
  þ linerel draws a line a relative distance from the current position (CP)
  þ lineto draws a line from the current position (CP) to (x,y)

 Declaration:
  þ void far line(int x1, int y1, int x2, int y2);
  þ void far linerel(int dx, int dy);
  þ void far lineto(int x, int y);

 Remarks:
þ line draws a line from (x1, y1) to (x2, y2) using the current color, line
style, and thickness. It does not update the current position (CP).

þ linerel draws a line from the CP to a point that is a relative distance
(dx, dy) from the CP, then advances the CP by (dx, dy).

þ lineto draws a line from the CP to (x, y), then moves the CP to (x, y).

 Return Value:  None

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  getlinesettings   setcolor          setlinestyle      setvisualpage
  setwritemode

 Examples:
  line example      linerel example   lineto example
