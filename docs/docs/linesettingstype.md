
  linesettingstype               <GRAPHICS.H>
 ßßßßßßßßßßßßßßßßßß
Used by getlinesettings and setlinestyle to adjust how lines are drawn.

  struct linesettingstype {
    int       linestyle;
    unsigned  upattern;
    int       thickness;
  };

  Element   ³ What It Is/Does
 ÍÍÍÍÍÍÍÍÍÍÍØÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍ
  upattern  ³ The user-defined bit pattern used when linestyle is set to
            ³ USERBIT_LINE.
  linestyle ³ Specifies in which style subsequent lines will be drawn
            ³ (such as solid, dotted, centered, dashed).
  thickness ³ Specifies whether the width of subsequent lines drawn will be
            ³ normal or thick. (enum line_widths)

upattern is a 16-bit pattern that applies only if linestyle is USERBIT_LINE
(4). In that case, whenever a bit in the pattern word is 1, the
corresponding pixel in the line is drawn in the current drawing color.

For example, a solid line corresponds to a upattern of 0xFFFF (all pixels
drawn), while a dashed line can correspond to a upattern of 0x3333 or 0x0F0F
or 0x3F3F.

   16-bit pattern  ³ upattern
 ÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍØÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍ
  ..xx..xx..xx..xx ³ 0x3333 (short dashes)
  ....xxxx....xxxx ³ 0x0F0F (long dashes)
  ..xxxxxx..xxxxxx ³ 0x3F3F (longer dashes)
  xxxxxxxxxxxxxxxx ³ 0xFFFF (solid line)
