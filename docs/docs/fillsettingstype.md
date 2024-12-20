---
uid: fillsettingstype
---
[!INCLUDE [](graphics_header.md)]
## &nbsp;fillsettingstype

Used to get current fill settings from [getfillsettings](getfillsettings.md).<br>

<div class="data">
  struct fillsettingstype {
    int  pattern;     /* current fill pattern */
    int  color;       /* current fill color */
  };
<br></div>

The functions bar, bar3d, fillpoly, pieslice, and floodfill all fill an area with the current fill pattern in the current fill color.<br><br>
If pattern = 12 (USER_FILL), a user-defined fill pattern is being used.<br><br>
Otherwise, pattern gives the number of a predefined pattern.<br><br>
There are 11 predefined fill pattern styles (solid, crosshatch, dotted, etc.).<br><br>
Symbolic names for the predefined patterns are provided by the enumerated type [fill_patterns](fill_patterns.md) in GRAPHICS.H. You can also define your own fill pattern.<br><br>
[Symbolic names for colors](COLORS.md) are also defined in GRAPHICS.H.<br>

<br>