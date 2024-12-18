
  fill_patterns                    <GRAPHICS.H>
 ÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜ

 Enum: Fill patterns for getfillsettings and setfillstyle.

  Names           ³Value³ Means Fill With...
 ÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍØÍÍÍÍÍØÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍ
  EMPTY_FILL      ³  0  ³ Background color
  SOLID_FILL      ³  1  ³ Solid fill
  LINE_FILL       ³  2  ³ ---
  LTSLASH_FILL    ³  3  ³ ///
  SLASH_FILL      ³  4  ³ ///, thick lines
  BKSLASH_FILL    ³  5  ³ \\\, thick lines
  LTBKSLASH_FILL  ³  6  ³ \\\
  HATCH_FILL      ³  7  ³ Light hatch
  XHATCH_FILL     ³  8  ³ Heavy crosshatch
  INTERLEAVE_FILL ³  9  ³ Interleaving lines
  WIDE_DOT_FILL   ³ 10  ³ Widely spaced dots
  CLOSE_DOT_FILL  ³ 11  ³ Closely spaced dots
  USER_FILL       ³ 12  ³ User-defined fill pattern

All but EMPTY_FILL fill with the current fill color. EMPTY_FILL uses the
current background color.
