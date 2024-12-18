
  fillsettingstype               <GRAPHICS.H>
 ßßßßßßßßßßßßßßßßßß
Used to get current fill settings from getfillsettings.

  struct fillsettingstype {
    int  pattern;     /* current fill pattern */
    int  color;       /* current fill color */
  };

The functions bar, bar3d, fillpoly, pieslice, and floodfill all fill an area
with the current fill pattern in the current fill color.

If pattern = 12 (USER_FILL), a user-defined fill pattern is being used.

Otherwise, pattern gives the number of a predefined pattern.

There are 11 predefined fill pattern styles (solid, crosshatch, dotted,
etc.).

Symbolic names for the predefined patterns are provided by the enumerated
type fill_patterns in GRAPHICS.H. You can also define your own fill pattern.

Symbolic names for colors are also defined in GRAPHICS.H.
